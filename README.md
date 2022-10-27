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
$ oc get compliancecheckresults -n openshift-compliance
```

## Scan With Auto Remediation

**IMPORTANT: DON'T RUN THIS ON A CLUSTER YOU CARE ABOUT! IT WILL ENFORCE EVERYTHING!**

**NOTE: If you scanned without remediation, delete the ScanSettingBinding
with:**

```bash
$ oc delete -f manifests/02-compliance-scan
```

### Perform a compliance scan with remediation

```bash
$ oc create -f manifests/03-compliance-remediation
```

### Monitor compliance scan

```bash
$ oc get compliancescan -w -n openshift-compliance
```

### Check scan results

```bash
$ oc get compliancecheckresults -n openshift-compliance
```

### Force compliance Re-scan

```bash
$ oc annotate compliancescans/ocp4-cis compliance.openshift.io/rescan=
$ oc annotate compliancescans/ocp4-cis-node-master compliance.openshift.io/rescan=
$ oc annotate compliancescans/ocp4-cis-node-worker compliance.openshift.io/rescan=
```

### Monitor compliance scan

```bash
$ oc get compliancescan -w -n openshift-compliance
```

### Check scan results

```bash
$ oc get compliancecheckresults -n openshift-compliance
```

