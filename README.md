# Install Certification Authority (to be able to access orc1 over HTTPS)
    scp paalmbj@orc1.ous.nsc.local:/data/common/repo/ca.crt /etc/pki/ca-trust/source/anchors/nsc.crt
    update-ca-trust

# Disable default online repository files
    cd /etc/yum.repos.d
    mkdir disabled
    mv *.repo disabled


# Install repo file & GPG key for EPEL
    scp paalmbj@orc1.ous.nsc.local:/etc/yum.repos.d/local-cent7.repo /etc/yum.repos.d/
    scp paalmbj@orc1.ous.nsc.local:/etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7 /etc/pki/rpm-gpg/RPM-GPG-KEY-EPEL-7

```bash
firewall-cmd --permanent --add-service=http
firewall-cmd --permanent --add-service=https
```

