# Base image
FROM python:3.12-slim AS base

# Set environment variables
ENV PYTHONDONTWRITEBYTECODE=1 \
    PYTHONUNBUFFERED=1

# Create a non-root user
RUN useradd -m appuser

# Set the working directory
WORKDIR /app

# Install system dependencies
# RUN apt-get update && apt-get install -y <dependencies> && apt-get clean

# The devstage sets up the stage that is used in the devcontainer. Here, code is not
# copied over, but instead mounted by VS Code, to ensure that changes in the container are
# also reflected in the source code.
FROM base AS development

# Set the working directory
WORKDIR /app

# Copy only the pyproject.toml and poetry.lock
COPY app/pyproject.toml ./
COPY app/README.md ./

# Install Poetry
RUN pip install poetry

# Install dependencies and generate poetry.lock
RUN poetry install --no-root --no-interaction --no-ansi

# Change ownership of the /app directory to appuser
RUN chown -R appuser:appuser /app

# Production stage
FROM base AS production

# Set the working directory
WORKDIR /app

# Copy the poetry.lock and pyproject.toml from the builder stage
COPY --from=development app/pyproject.toml ./
#COPY --from=development ./poetry.lock ./
COPY --from=development app/README.md ./

# Install only production dependencies
RUN poetry install --no-dev --no-interaction --no-ansi

# Copy the application code from the builder stage (excluding tests for production)
COPY --from=developoment app/src/ ./src/

RUN chown -R appuser:appuser /app

# Switch to non-root user
USER appuser

# Specify the default command
CMD ["poetry", "run", "python", "src/app/main.py"]  # Adjust to your entry point if needed

