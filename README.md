# Dockerfile Bug: Missing Dependencies in Test Environment

This repository demonstrates a common error in Dockerfiles: installing dependencies after copying the application code.  This results in the tests failing because the necessary packages are missing.

The `Dockerfile` shows the incorrect order of commands, while `Dockerfile_fixed` provides the corrected version.

## How to Reproduce

1. Clone this repository.
2. Build the original Dockerfile: `docker build -f Dockerfile -t test-image .`
3. Attempt to run the tests: `docker run test-image` (This will fail)
4. Build the corrected Dockerfile: `docker build -f Dockerfile_fixed -t test-image-fixed .`
5. Run the tests with the corrected Dockerfile: `docker run test-image-fixed` (This should pass)

## Solution

The corrected Dockerfile (`Dockerfile_fixed`) ensures that dependencies are installed *before* the application code is copied into the container. This guarantees that the application has everything it needs to run successfully.