# Build Attempt Tracking

This document tracks different build attempts with various environment configurations for the Nucleus CDK test repository.

## Build Attempts

| Attempt | Environment File | Python Version | Key Dependencies | Public Binder | CurveNote Binder | Local Conda | Local Poetry | Notes |
|---------|------------------|----------------|------------------|----------------|------------------|-------------|--------------|-------|
| 1 | `trys/environment-py3.13-public-fail/environment.yml` | 3.13.5 | nucleus-cdk=0.3.0a1, numpy=2.3.1, scipy=1.16.0 | ❌ Failed | ❌ Failed | ✅ Success | ✅ Success | Python 3.13 too new for Binder |
| 2 | `environment.yml` | 3.12.x | nucleus-cdk=0.3.0a1, numpy=2.3.1, scipy=1.16.0 | ⏳ Pending | ⏳ Pending | ✅ Success | ✅ Success | Python 3.12 should work on Binder |
| 3 | TBD | TBD | TBD | TBD | TBD | TBD | TBD | TBD |

## Environment Details

### Attempt 2: Python 3.12.x
- **File**: `environment.yml`
- **Python**: 3.12.x
- **Key Packages**:
  - nucleus-cdk=0.3.0a1
  - numpy=2.3.1
  - scipy=1.16.0
  - matplotlib=3.10.3
  - jupyterlab=4.3.5
  - ipympl=0.9.7
  - ipywidgets=8.1.5
  - hvplot=0.11.3
  - seaborn=0.13.2
  - scikit-image=0.25.2
  - rich=14.0.0 (adjusted to >=13.9.2,<14.0.0 for Poetry)

**Results**:
- ✅ **Local Conda**: Built successfully
- ✅ **Local Poetry**: Built successfully  
- ⏳ **Public Binder**: Pending test
- ⏳ **CurveNote Binder**: Pending test

**Issues Identified**:
- Rich dependency conflict resolved by adjusting version constraint
- Python 3.12 should be compatible with Binder infrastructure

### Attempt 1: Python 3.13.5
- **File**: `trys/environment-py3.13-public-fail/environment.yml`
- **Python**: 3.13.5
- **Key Packages**:
  - nucleus-cdk=0.3.0a1
  - numpy=2.3.1
  - scipy=1.16.0
  - matplotlib=3.10.3
  - jupyterlab=4.3.5
  - ipympl=0.9.7
  - ipywidgets=8.1.5
  - hvplot=0.11.3
  - seaborn=0.13.2
  - scikit-image=0.25.2

**Results**:
- ✅ **Local Conda**: Built successfully
- ✅ **Local Poetry**: Built successfully  
- ❌ **Public Binder**: Failed (likely Python 3.13 too new)
- ❌ **CurveNote Binder**: Failed (likely Python 3.13 too new)

**Issues Identified**:
- Python 3.13.5 is too recent for Binder infrastructure
- Need to downgrade to Python 3.12 or 3.11 for Binder compatibility

## Next Steps

1. **Attempt 2**: Try Python 3.12.x with same dependencies
2. **Attempt 3**: Try Python 3.11.x if 3.12 still fails
3. **Attempt 4**: Consider removing some dependencies if still failing

## Binder Infrastructure Notes

- Public Binder typically supports Python 3.8-3.11
- CurveNote Binder may have similar limitations
- Local builds work because they use current Python versions
- Need to balance between latest features and Binder compatibility 