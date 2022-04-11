# Compliance Operator Walkthrough

## Install Compliance Operator

```bash
$ oc create -f manifests/01-operator
```

## Scan Without Remediation

### Perform a compliance scan

```bash
$ oc create -f manifests/02-compliance-scan
```

### Monitor compliance scan

```bash
$ oc get compliancescan -w -n openshift-compliance
```

### Check scan results

```bash
$ oc get compliancecheckresults
```

## Scan With Auto Remediation

**NOTE: If you scanned without remediation, delete the ScanSettingBinding
with:**

```bash
$ oc delete -f manifests/02-compliance-scan
```

### Perform a compliance scan with remediation

```bash
$ oc create -f manifests/03-compliance-remediation
```
