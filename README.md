# Galaxy Extensions (Ansible role)

A collection of Galaxy extensions (AKA webhooks) in an Ansible role for rapid
deployment to Galaxy servers


Extension       | Author    | Responsibility
--------------- | --------- | --------------
citation_needed | Galaxy EU | Shows how to cite us randomly after jobs
gtn             | Galaxy EU | Embed GTN in Galaxy
iframe          | Galaxy EU | Shows a random iframe after jobs
phdcomics       | Galaxy EU | Shows a random phd comic after jobs
search          | Galaxy EU | Shows the search interface
tool_list       | Galaxy EU | Adds a button to generate the tool list
tour_generator  | Galaxy EU | Adds support for tour generator
lab_switcher    | Galaxy AU | Easily navigate between Galaxy Labs
toolmsg         | Galaxy AU | User-facing messages on specific tools
tips            | Galaxy AU | Show random Galaxy tip after jobs


## Directory structure

Each extension is versioned by Galaxy version, to accomodate breaking changes in
Galaxy releases. The Ansible role should install the highest version available
that is less than or equal to the Galaxy version on the host.


## Templating

Any extension can be templated by adding a .j2 extension to the file name. Any
variables available in the running playbook can be used, but defaults should be
set in defaults/extensions.yml to ensure predictable results, and document the
variables being used for users of the Ansible role.


## Testing

This role includes comprehensive tests:

- **Unit tests** - Test the custom Ansible module logic
- **Integration tests** - Test the full role execution using Molecule
- **Linting** - YAML and Ansible best practices

### Quick Start

```bash
# Install test dependencies
pip install -r requirements-test.txt

# Run all tests
make test

# Run specific test types
make test-unit        # Unit tests only
make test-molecule    # Integration tests only
make lint            # Linting only
```

See [TESTING.md](TESTING.md) for detailed testing documentation.

### Test Scenarios

- **default** - Basic functionality and idempotency
- **templating** - Jinja2 template variable rendering
- **versions** - Galaxy version selection logic

### CI/CD

Tests run automatically via GitHub Actions on push and pull requests.
