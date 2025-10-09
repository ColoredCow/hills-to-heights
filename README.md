# Hills to Heights

## Development Practices

Our workflow ensures every change is developed locally, reviewed in a shared environment, and released to production in a controlled manner.

### Environment Flow

| Environment | Purpose | Source Branch | Hosted On |
|--------------|----------|----------------|------------|
| **Local (Developer Machines)** | Active feature development and testing | `feature/*` | Developer’s system (macOS / Windows) |
| **UAT (Staging)** | Internal QA and client demos | `develop` | AWS EC2 (Staging Server) |
| **Production** | Public live site for end users | `main` | AWS EC2 (Production Server) |

#### Flow Summary
1. Developers work locally and push to feature branches.  
2. Once ready, code is merged into `develop`, which is deployed to UAT.  
3. After review and QA, stable code is merged to `main` and deployed to production.  
4. Deployments are manual for now, but CI/CD automation (via GitHub Actions) will follow.
