# Copilot Instructions for `digest-service`

## Overview
This repository is a test repo for BMAD V4, focusing on modular development with expansion packs for specific capabilities like infrastructure and DevOps. The structure is designed to support various roles and workflows, ensuring seamless integration and collaboration.

## Repository Structure
- **`web-bundles/agents/`**: Contains role-specific agent configurations (e.g., `analyst.txt`, `architect.txt`).
- **`web-bundles/teams/`**: Defines team configurations (e.g., `team-all.txt`, `team-no-ui.txt`).
- **`web-bundles/expansion-packs/`**: Includes additional capabilities like game development and infrastructure DevOps.
- **`.bmad-infrastructure-devops/`**: Focuses on infrastructure and DevOps workflows, including CI/CD and cloud resource management.

## Key Workflows
1. **Building and Testing**:
   - Ensure all dependencies are installed before running builds.
   - Use the provided scripts or tasks for testing and validation.

2. **Debugging**:
   - Follow the logs generated in the `logs/` directory for debugging issues.
   - Use the `devops.ide.md` for IDE-specific debugging configurations.

3. **Infrastructure and DevOps**:
   - Refer to `.bmad-infrastructure-devops/README.md` for setting up Kubernetes, GitOps, and IaC workflows.
   - Use `devops.yaml` for configuring DevOps agents.

## Project-Specific Conventions
- **File Naming**:
  - Use descriptive names for agents and team configurations.
  - Follow the naming conventions in `web-bundles/` for consistency.
- **Documentation**:
  - Update relevant `README.md` files when making structural changes.

## Integration Points
- **External Dependencies**:
  - Ensure compatibility with cloud platforms and CI/CD tools as outlined in `.bmad-infrastructure-devops/README.md`.
- **Cross-Component Communication**:
  - Use the team configurations in `web-bundles/teams/` to define communication patterns.

## Examples
- **Adding a New Agent**:
  - Place the configuration file in `web-bundles/agents/`.
  - Update the relevant team file in `web-bundles/teams/` to include the new agent.

- **Setting Up a DevOps Workflow**:
  - Use the `devops.yaml` file in `.bmad-infrastructure-devops/`.
  - Follow the CI/CD pipeline setup instructions in `.bmad-infrastructure-devops/README.md`.

## Notes
- Always validate changes in a local environment before pushing to the main branch.
- For detailed instructions, refer to the `README.md` files in the respective directories.
