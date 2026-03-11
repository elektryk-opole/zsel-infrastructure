# Contributing to zsel-infrastructure

Welcome to infrastructure contributions! This guide covers hardware documentation and IaC.

## Getting Started

1. **Fork** the repository
2. **Clone** to your local machine
3. **Create a branch** with descriptive name
4. **Make changes** with proper documentation
5. **Submit pull request**

## Infrastructure Changes

### Documentation Changes

For hardware or network changes:
1. Update relevant .md file
2. Include before/after state
3. Document procedure and timeline
4. List affected systems
5. Include rollback procedure

### Terraform Changes

```bash
# Format code
terraform fmt

# Validate syntax
terraform validate

# Plan changes
terraform plan -out=tfplan

# Review plan carefully before applying
terraform show tfplan
```

## Change Management

### Procedure
1. **Create issue** describing the change
2. **Design review**: Get team approval
3. **Test in staging**: Verify functionality
4. **Plan maintenance window**: If production impact
5. **Implement change**: Apply Terraform or update docs
6. **Verify**: Test all affected systems
7. **Document**: Update runbooks and diagrams also

### Rollback Plan
Every change must include:
- How to revert the change
- Time to roll back
- Who to contact if issues
- Data backup location

## Hardware Documentation

### Adding New Hardware
1. Document specifications
2. Update capacity planning
3. Plan integration testing
4. Schedule installation
5. Update network topology
6. Update monitoring

### Removing Hardware
1. Migrate workloads
2. Archive configuration backups
3. Document decommission date
4. Remove from monitoring
5. Update capacity docs

## Disaster Recovery Testing

Test recovery procedures:
- [ ] Monthly backup restoration
- [ ] Quarterly full DR test
- [ ] Annual failover test
- [ ] Document any issues found
- [ ] Update procedures as needed

## Security Considerations

- Never commit credentials
- Encrypt sensitive documentation
- Restrict access appropriately
- Audit all infrastructure changes
- Document security implications

## Performance Testing

For significant changes:
1. Establish baseline metrics
2. Implement change
3. Measure impact
4. Document findings
5. Adjust if needed

## Code Standards

### Documentation
- Use clear, technical language
- Include diagrams
- Document all assumptions
- Explain why, not just what

### Terraform
- Use consistent naming
- Include descriptions
- Add comments for complexity
- Use variables for configuration

## Review Process

Reviewers will check:
- [ ] Change purpose is clear
- [ ] Implementation is sound
- [ ] Risk is identified
- [ ] Rollback plan exists
- [ ] Documentation is complete
- [ ] Security reviewed
- [ ] Performance impact assessed

## Questions?

- **Documentation**: See [documentation/](documentation/)
- **Help**: infrastructure-team@zsel.opole.pl
- **Discussions**: GitHub discussions

---

Thank you for keeping our infrastructure solid! 🏗️
