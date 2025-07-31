# Nucleus CDK Test Repository

This repository is used to test Binder deployments with different Python environment configurations for the Nucleus CDK package.

## Project Structure

```
vpin-test/
├── environment.yml                        # Current attempt (Python 3.12)
├── pyproject.toml                        # Poetry config for Python 3.12
├── poetry.lock                           # Poetry lock file
├── trys/                                 # Previous attempts
│   └── environment-py3.13-public-fail/   # Attempt 1: Python 3.13.5
│       ├── environment.yml               # Conda environment file
│       ├── pyproject.toml                # Poetry configuration
│       └── poetry.lock                   # Poetry lock file
├── hello-world.ipynb                     # Test notebook
├── build-tracking.md                     # Build attempt tracking
└── .gitignore                            # Git ignore rules
```

## Current Status

### Attempt 2: Python 3.12.x (Current)
- **Location**: Root directory (`environment.yml`)
- **Status**: ⏳ Pending Binder tests
- **Local**: ✅ Works with both Conda and Poetry
- **Key Fix**: Resolved rich dependency conflict

### Attempt 1: Python 3.13.5
- **Location**: `trys/environment-py3.13-public-fail/`
- **Status**: ❌ Failed on Binder (Python 3.13 too new)
- **Local**: ✅ Works with both Conda and Poetry

## Next Steps

1. **Test on Binder**: Deploy current Python 3.12 environment
2. **Attempt 3**: Try Python 3.11.x if 3.12 still fails
3. **Attempt 4**: Consider dependency optimization

## Testing

To test the current environment:

```bash
# Test with Conda
conda env create -f environment.yml
conda activate vpin-test-py3.12

# Test with Poetry
poetry install
poetry run python -c "import cdk; print('Success!')"
```

## Binder Deployment

Each attempt can be tested on:
- Public Binder: `https://mybinder.org`
- CurveNote Binder: `https://binder.curvenote.com`

See `build-tracking.md` for detailed results and notes. 