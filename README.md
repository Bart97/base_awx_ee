# My base Execution Environment for AWX

## Setup

1. Download [Dell iDRAC tools for Linux](https://www.dell.com/support/home/en-us/drivers/driversdetails?driverid=rdcvd), version doesn't really matter as long as it still includes idracadm7.
2. Extract the package, find RHEL7 variant of idracadm7 and argtable2 RPM.
3. Extract the RPM packages:

    ```
    rpmextract.sh ./linux/rac/RHEL7/x86_64/srvadmin-argtable2-9.2.0-3142.13664.el7.x86_64.rpm
    rpmextract.sh ./linux/rac/RHEL7/x86_64/srvadmin-idracadm7-9.2.0-3142.13664.el7.x86_64.rpm
    ```

4. Copy the following files to project root/context:
    - opt/dell/srvadmin/lib64/openmanage/private/libargtable2.so.0
    - opt/dell/srvadmin/bin/idracadm7

5. Build the image. Remember to source the Python venv

    ```
    source ansible-builder-venv/bin/activate
    ansible-builder build --tag quay.io/bkazmierczak/base_awx_ee
    ```
