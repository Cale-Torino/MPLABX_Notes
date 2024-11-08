# MPLABX Notes & Tips, Tricks etc

For 4K screens Netbeans looks fugly so in order to fix this we need to applie some manual fixes..

## Fixing 4k DPI Issue

## Step 1

If you installed MPLABX in the default position e.g:

```
C:\Program Files\Microchip\MPLABX\v6.15\mplab_platform\etc
```
Browse to this dir and open the `mplab_ide.conf` config file.

find the `default_options=` string and add `-J-Dsun.java2d.dpiaware=true` to the end.

you can also add `-J-Dsun.java2d.dpiaware=true --fontsize 24`

E.G

Replace

```
default_options="-J-Dmymicrochip.connect=false -J-Dstatistics.connect=false -J-Dcore.properties.disableHttpProxy=true -J-Dprism.allowhidpi=false --branding mplab -J-Dcrownking.stream.verbosity=very-quiet -J-Xss2m -J-Xms256m -J-Xmx8171m -J-Dapple.awt.graphics.UseQuartz=true -J-XX:+UseConcMarkSweepGC -J-XX:+CMSClassUnloadingEnabled -J-Dapt.limit.expanded.params=1000 -J-Dplugin.manager.check.interval=EVERY_STARTUP -J-Dsun.java2d.noddraw=true -J-Dorg.netbeans.modules.extbrowser.UseDesktopBrowse=true -J-Dnetbeans.importclass=org.netbeans.upgrade.AutoUpgrade"
```

With

```
default_options="-J-Dmymicrochip.connect=false -J-Dstatistics.connect=false -J-Dcore.properties.disableHttpProxy=true -J-Dprism.allowhidpi=false --branding mplab -J-Dcrownking.stream.verbosity=very-quiet -J-Xss2m -J-Xms256m -J-Xmx8171m -J-Dapple.awt.graphics.UseQuartz=true -J-XX:+UseConcMarkSweepGC -J-XX:+CMSClassUnloadingEnabled -J-Dapt.limit.expanded.params=1000 -J-Dplugin.manager.check.interval=EVERY_STARTUP -J-Dsun.java2d.noddraw=true -J-Dorg.netbeans.modules.extbrowser.UseDesktopBrowse=true -J-Dnetbeans.importclass=org.netbeans.upgrade.AutoUpgrade -J-Dsun.java2d.dpiaware=true"
```

Example of file with modification

```CONF
# DO NOT ALTER OR REMOVE COPYRIGHT NOTICES OR THIS HEADER.
#
# Copyright 2005, 2016 Oracle and/or its affiliates. All rights reserved.
#
# Oracle and Java are registered trademarks of Oracle and/or its affiliates.
# Other names may be trademarks of their respective owners.
#
# The contents of this file are subject to the terms of either the GNU
# General Public License Version 2 only ("GPL") or the Common
# Development and Distribution License("CDDL") (collectively, the
# "License"). You may not use this file except in compliance with the
# License. You can obtain a copy of the License at
# http://www.netbeans.org/cddl-gplv2.html
# or nbbuild/licenses/CDDL-GPL-2-CP. See the License for the
# specific language governing permissions and limitations under the
# License.  When distributing the software, include this License Header
# Notice in each file and include the License file at
# nbbuild/licenses/CDDL-GPL-2-CP.  Oracle designates this
# particular file as subject to the "Classpath" exception as provided
# by Oracle in the GPL Version 2 section of the License file that
# accompanied this code. If applicable, add the following below the
# License Header, with the fields enclosed by brackets [] replaced by
# your own identifying information:
# "Portions Copyrighted [year] [name of copyright owner]"
#
# If you wish your version of this file to be governed by only the CDDL
# or only the GPL Version 2, indicate your decision by adding
# "[Contributor] elects to include this software in this distribution
# under the [CDDL or GPL Version 2] license." If you do not indicate a
# single choice of license, a recipient has the option to distribute
# your version of this file under either the CDDL, the GPL Version 2 or
# to extend the choice of license to its licensees as provided above.
# However, if you add GPL Version 2 code and therefore, elected the GPL
# Version 2 license, then the option applies only if the new code is
# made subject to such option by the copyright holder.

# Default locations of userdir and cachedir:
# (http://wiki.netbeans.org/FaqWhatIsUserdir)
#
# On Windows ${DEFAULT_USERDIR_ROOT} will be replaced by the launcher
# with "<AppData>\***unknown variable appname***" where <AppData> is user's
# value of "AppData" key in Windows Registry under
# "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Shell Folders"
# and ${DEFAULT_CACHEDIR_ROOT} will be replaced by the launcher
# with "<Local AppData>\NetBeans\Cache" where <Local AppData> is user's
# value of "Local AppData" key in Windows Registry under
# "HKCU\Software\Microsoft\Windows\CurrentVersion\Explorer\Shell Folders"
#
# On Mac ${DEFAULT_USERDIR_ROOT} will be replaced by the launcher
# with "~/Library/Application Support/***unknown variable appname***" and
# ${DEFAULT_CACHEDIR_ROOT} with "~/Library/Caches/***unknown variable appname***"
#
# On other systems ${DEFAULT_USERDIR_ROOT} will be replaced by the launcher
# with "~/.***unknown variable appname***" and ${DEFAULT_CACHEDIR_ROOT} with "~/.cache/***unknown variable appname***"
#
# You can also use ${HOME} variable which will be replaced with
# user.home JVM system property value. This variable is valid only in
# default_userdir and default_cachedir properties.
#
# NOTE: If you specify a non-default userdir path on command line
# (--userdir option) and don't specify a cachedir path (--cachedir option),
# cachedir will be in "<userdir>/var/cache".
#

default_userdir="${DEFAULT_USERDIR_ROOT}/dev/v6.15"
default_cachedir="${DEFAULT_CACHEDIR_ROOT}/dev/v6.15/var"


# Options used by the launcher by default:
# (can be overridden by explicit command line switches)
#
# Note that default -Xmx is selected for you automatically.
# You can find these values in var/log/messages.log file in your userdir.
# The automatically selected value can be overridden by specifying -J-Xmx
# here or on the command line.
#
# If you specify the heap size explicitly, you may also want to enable
# Concurrent Mark & Sweep garbage collector.
# (see http://wiki.netbeans.org/FaqGCPauses)
#
# In the following default_options line, the -J-Xmx option specifying the max heap 
# space (the max amount of memory MPLAB X can use) is not included. This is because the JRE itself will look at 
# the environment where it is being run and will select an appropriate value. This value is typically 1/4 of the 
# max amount of memory in the system. If you want to allocate a larger value for the amount of memory
# you can add -J-XmxVALUE. For example, -J-Xmx4096m will make the upper limit be 4 gigabytes.

default_options="-J-Dmymicrochip.connect=false -J-Dstatistics.connect=false -J-Dcore.properties.disableHttpProxy=true -J-Dprism.allowhidpi=false --branding mplab -J-Dcrownking.stream.verbosity=very-quiet -J-Xss2m -J-Xms256m -J-Xmx8171m -J-Dapple.awt.graphics.UseQuartz=true -J-XX:+UseConcMarkSweepGC -J-XX:+CMSClassUnloadingEnabled -J-Dapt.limit.expanded.params=1000 -J-Dplugin.manager.check.interval=EVERY_STARTUP -J-Dsun.java2d.noddraw=true -J-Dorg.netbeans.modules.extbrowser.UseDesktopBrowse=true -J-Dnetbeans.importclass=org.netbeans.upgrade.AutoUpgrade -J-Dsun.java2d.dpiaware=false"

# Default location of JDK:
# (set by installer or commented out if launcher should decide)
#
# It can be overridden on command line by using --jdkhome <dir>
# Be careful when changing jdkhome.
# There are two NetBeans launchers for Windows (32-bit and 64-bit) and
# installer points to one of those in the NetBeans application shortcut 
# based on the Java version selected at installation time.
#
jdkhome="C:\Program Files\Microchip\MPLABX\v6.15\sys\java\zulu8.64.0.19-ca-fx-jre8.0.345-win_x64\"

# Additional module clusters:
# using ${path.separator} (';' on Windows or ':' on Unix):
#
#extra_clusters="/absolute/path/to/cluster1:/absolute/path/to/cluster2"

```

## Step 2

go to the dir `C:\Program Files\Microchip\MPLABX\v6.15\mplab_platform\bin\`

right click on `mplab_ide64.exe` and select `properties` then select `compatilility`

now click on the `Change high DPI settings`

check the checkbox called `Override high DPI scaling behaviour`.

Tick Overide high DPI scaling and choose System or System (Enhanced) in the dropbox.

Click ok finally click Apply.

Now the `DPI` should look good but the scaling can be small to read.









# Links
- [scaling-issues-with-mplabxide](https://stackoverflow.com/questions/59381656/how-do-you-fix-scaling-issues-with-mplabxide-with-mcc-in-windows-10-when-using)
- [monitors](https://developerhelp.microchip.com/xwiki/bin/view/software-tools/ides/x/configuration/monitors/)
-https://www.eevblog.com/forum/microcontrollers/alternative-(better!)-ide-to-mplab-x/25/
-
-



