#!/bin/bash

# Exit immediately if a command exits with a non-zero status
set -e

# Define colors for output
GREEN='\033[0;32m'
BLUE='\033[0;34m'
RED='\033[0;31m'
NC='\033[0m' # No Color

echo -e "${BLUE}--- Starting Flutter Quality Check ---${NC}"

# 1. Get Dependencies
echo -e "\n${BLUE}Step 1: Fetching dependencies...${NC}"
flutter pub get

# 2. Run Static Analysis (Linting)
echo -e "\n${BLUE}Step 2: Checking linting (static analysis)...${NC}"
if flutter analyze; then
    echo -e "${GREEN}✓ No analysis issues found.${NC}"
else
    echo -e "${RED}✗ Linting issues detected! Please fix them before proceeding.${NC}"
    exit 1
fi

# 3. Run Unit Tests
echo -e "\n${BLUE}Step 3: Running unit tests...${NC}"
if flutter test --no-pub; then
    echo -e "${GREEN}✓ All tests passed.${NC}"
else
    echo -e "${RED}✗ Some tests failed!${NC}"
    exit 1
fi

echo -e "\n${GREEN}--- All checks passed successfully! ---${NC}"