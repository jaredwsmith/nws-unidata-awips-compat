# Installing AWIPS 19.3.1 from the ADE-provided binaries

WARNING: May cause hair loss. (Kidding. Kind of.)

NOTE: This is largely reconstructed from `.bash_history` and other attempts at recollection and may not be 100% accurate. Lots of trial and error here.


Due to an upload error at NWS, the OB19.3.1-NBL.tgz file up at the AWIPS Technical Library is actually
[19.2.5](https://vlab.ncep.noaa.gov/web/awips-technical-library/home/-/blogs/issue-with-19-3-1-binaries?_com_liferay_blogs_web_portlet_BlogsPortlet_redirect=https%3A%2F%2Fvlab.ncep.noaa.gov%3A443%2Fweb%2Fawips-technical-library%2Fhome%3Fp_p_id%3Dcom_liferay_blogs_web_portlet_BlogsPortlet%26p_p_lifecycle%3D0%26p_p_state%3Dnormal%26p_p_mode%3Dview%26_com_liferay_blogs_web_portlet_BlogsPortlet_cur%3D1%26_com_liferay_blogs_web_portlet_BlogsPortlet_delta%3D50). However, the files for the AWIPS Development Environment (ADE) do contain 19.3.1 binaries that work just fine, it's just that the installation process needs a little massaging. And since I write this in the midst of a global pandemic, we need to make do with what we have.

## Don't bother with `ade_quick_install.sh`

The first thing to know about this process is that `ade_quick_install.sh` is largely not usable (at least on machines available to non-NWS mortals). There are package conflicts out the wazoo; you are better off issuing the yum commands directly. I was able to attain a successful installation by using roughly the following steps.

## To install

1. We are going to first need to rename a few conflicting binary packages. I opted to favor the WFO-level install, eschewing a few of the NCEP packages that are provided. These are the files I had to rename:  

	- `awips2-cave-gfeclient-19.3.1-30.x86_64.rpm`
	- `awips2-cave-ncep-19.3.1-30.x86_64.rpm`
	- `awips2-database-server-configuration-19.3.1-30.noarch.rpm`
	- `awips2-ncep-cli-19.3.1-30.noarch.rpm`
	- `awips2-ncep-database-19.3.1-30.noarch.rpm`
	- `awips2-ncep-gempak-19.3.1-30.x86_64.rpm`  

	The best way to go about renaming these is to change their file extensions from `rpm` to `disabled`. Worked like a champ.  

2. We'll then need to manually execute a `yum` command to install the remaining packages:

    `yum --disablerepo=* install *.rpm --nogpgcheck -y --skip-broken`
    
    This command will install not only a functioning CAVE, but will also install EDEX as well as the rest of the ADE if you want to poke around.
    
3. (Optional) Unzip the `awips2-ade-baseline-SOURCES.jar` file to `/home/<youruser>/awips` to get at the source code. The Archive Manager within the CentOS GUI is just fine for this task.

## If these didn't work...

...please file an issue with what you're experiencing!