# CI/CD Practice Repository

A comprehensive GitHub Actions learning repository showcasing various CI/CD concepts and workflow patterns. This repo contains multiple workflow examples demonstrating different aspects of continuous integration and deployment.

## 📋 Overview

This repository is designed as a learning resource for understanding GitHub Actions workflows. It includes practical examples covering:

- **Basic Workflows**: Simple job execution and echoing output
- **Job Dependencies**: Using `needs` to orchestrate sequential job execution
- **Conditional Logic**: Running jobs based on branch, event type, and custom conditions
- **Event Triggers**: Different GitHub events that trigger workflows (push, pull requests)
- **Docker Integration**: Container-based CI practices
- **Reusable Workflows**: Creating modular, reusable workflow components
- **Advanced Features**: Inputs, outputs, environments, and secrets handling

## 📁 Repository Structure

```
.github/
└── workflows/
    ├── hello.yml                 # Basic workflow with job dependencies
    ├── main.yml                  # Branch-specific triggers
    ├── build-deploy.yml          # Build and deployment workflow
    ├── docker-ci.yml             # Docker integration example
    ├── reusable.yml              # Reusable workflow template
    ├── pr.yml                    # Pull request workflows
    ├── checkout.yml              # Repository checkout examples
    ├── commit.yml                # Git commit operations
    ├── env.yml                   # Environment variables
    ├── secrets.yml               # Secrets management
    ├── if.yml                    # Conditional execution
    ├── inputs-demo.yml           # Workflow inputs
    ├── outputs-demo.yml          # Workflow outputs
    ├── call-workflow.yml         # Calling workflows
    ├── call-tests.yml            # Test invocation patterns
    ├── artifacts.yml             # Artifact handling
    ├── setup.yml                 # Initial setup tasks
    ├── success.yml               # Success notifications
    └── blank.yml                 # Template starter
```

## 🔄 Key Workflows

### 1. **hello.yml** - Basic Workflow with Dependencies
Demonstrates fundamental workflow structure and job sequencing.

```yaml
- Job "build1" runs first with a simple echo
- Job "workf" depends on build1 (uses `needs`)
```

**Use case**: Understanding how to orchestrate sequential jobs.

---

### 2. **main.yml** - Branch-Specific Triggers
Shows conditional workflow execution based on git branch.

```yaml
- Triggers on push events
- Only executes if pushing to main branch
- Uses conditional: if: github.ref == 'refs/heads/main'
```

**Use case**: Running specific jobs only on production branches.

---

### 3. **build-deploy.yml** - Build and Deployment Pipeline
Demonstrates a complete CI/CD pipeline with separate build and deploy stages.

```yaml
- Build Job: Runs only on pull requests
- Deploy Job: Runs only on push to main branch
```

**Use case**: Separating testing/building from production deployment.

---

### 4. **docker-ci.yml** - Docker Integration
Complete Docker workflow example with container management.

```yaml
- Pulls official nginx Docker image
- Runs container with port mapping
- Performs health checks
- Inspects container metadata
```

**Use case**: Testing applications in containerized environments.

---

### 5. **reusable.yml** - Reusable Workflows
Template workflow that can be called from other workflows using `workflow_call`.

```yaml
- Defines reusable job components
- Can be imported by other workflows
- Promotes code reuse across workflows
```

**Use case**: Creating shared workflow templates.

---

## 🚀 Getting Started

### Prerequisites
- GitHub repository with Actions enabled
- Basic understanding of YAML syntax
- GitHub account with repository access

### How to Use

1. **Clone or fork this repository**
   ```bash
   git clone https://github.com/24311a04eg-lgtm/ci-cd-practice.git
   cd ci-cd-practice
   ```

2. **Push changes to trigger workflows**
   ```bash
   git push origin main
   ```

3. **Monitor workflow execution**
   - Navigate to the **Actions** tab in your repository
   - Select a workflow to view execution details
   - Check logs for each job and step

### Exploring Workflows

Each workflow file demonstrates specific concepts:

- **Start simple**: Begin with `hello.yml` and `main.yml`
- **Progress to advanced**: Move to `build-deploy.yml` and `docker-ci.yml`
- **Learn patterns**: Study `reusable.yml` for creating modular workflows

## 🎯 Learning Path

| Level | Workflows | Concepts |
|-------|-----------|----------|
| **Beginner** | hello.yml, main.yml | Basic triggers, job dependencies, conditionals |
| **Intermediate** | build-deploy.yml, docker-ci.yml | Event filtering, Docker integration, pipelines |
| **Advanced** | reusable.yml, call-*.yml | Workflow reuse, inputs/outputs, composition |
| **Expert** | secrets.yml, artifacts.yml, env.yml | Sensitive data, artifact management, environments |

## 📝 Workflow Concepts Covered

### Event Triggers
- `push` - Triggered on code push
- `pull_request` - Triggered on PR creation/update
- `workflow_call` - Makes workflow reusable

### Conditional Execution
- Branch filtering: `refs/heads/main`
- Event type filtering: `github.event_name`
- Custom conditions: `if` statements

### Job Orchestration
- Sequential execution using `needs`
- Parallel job execution
- Conditional job skipping

### Docker Operations
- Image pulling and caching
- Container runtime management
- Health checks and verification

### Best Practices
- Clear job naming
- Descriptive step names
- Conditional logic for environment-specific actions
- Proper artifact and secret handling

## 🔧 Customization

To adapt these workflows for your projects:

1. **Modify triggers**: Update `on:` section for your events
2. **Change commands**: Replace `run:` scripts with your actual build commands
3. **Add environment variables**: Use `env:` for configuration
4. **Integrate secrets**: Reference secrets in workflows (configured in repo settings)
5. **Combine workflows**: Mix and match workflow patterns for your use case

## 📚 GitHub Actions Documentation

For detailed information, refer to:
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Workflow Syntax Reference](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions)
- [Events that Trigger Workflows](https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows)

## 🐳 Docker Integration Details

The `docker-ci.yml` workflow demonstrates:
- Pulling pre-built images from Docker Hub
- Running containers with custom configurations
- Port mapping for accessibility
- Container health verification
- Log inspection for troubleshooting

### Example: Running nginx
```bash
docker pull nginx                              # Pull image
docker run -d -p 8080:80 --name mynginx nginx # Run container
docker ps -a                                  # List containers
curl http://localhost:8080                    # Health check
```

## 💡 Common Patterns

### Pattern 1: Main Branch Protection
```yaml
if: github.ref == 'refs/heads/main'
```

### Pattern 2: PR-Only Testing
```yaml
if: github.event_name == 'pull_request'
```

### Pattern 3: Job Dependencies
```yaml
needs: previous-job-name
```

### Pattern 4: Docker Operations
```yaml
docker pull IMAGE
docker run [options] IMAGE
```

## 📊 Repository Statistics

- **Language Composition**: 97.7% HTML, 2.3% JavaScript
- **Total Workflows**: 21 different workflow files
- **Focus**: CI/CD learning and GitHub Actions patterns

## 🤝 Contributing

This is a learning repository. Feel free to:
- Fork and experiment with the workflows
- Create variations to test different concepts
- Submit pull requests with new workflow examples

## ⚡ Quick Start Commands

```bash
# View workflow status
gh workflow list

# View specific workflow runs
gh run list --workflow=hello.yml

# View workflow logs
gh run view RUN_ID --log

# Trigger a workflow (if supported)
gh workflow run hello.yml
```

## 🔐 Security Notes

- Never commit secrets to the repository
- Use GitHub repository secrets for sensitive data
- Reference secrets as `${{ secrets.SECRET_NAME }}`
- Keep workflows in version control
- Review external actions for security

## 📞 Support

For issues or questions:
1. Check GitHub Actions logs in the Actions tab
2. Review workflow syntax and error messages
3. Consult GitHub documentation
4. Enable debugging with: `runner.debug=true`

## 📄 License

This repository is public and available for learning purposes.

---

**Last Updated**: June 2026

Happy learning! Explore, experiment, and master GitHub Actions! 🚀
