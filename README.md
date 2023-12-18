# cmpe-283-assignment-3 (0x4FFFFFFD, 0x4FFFFFFC)

## Q1. For each member in your team, provide 1 paragraph detailing what parts of the lab that member implemented / researched.

- ## Mohaimin Iqbal Gazi
  -
  -
  -
  -
- ## Hemang Huria
  -
  -
  -
  -

## Q2. Describe in detail the steps you used to complete the assignment.

- Use the virtual instance we created in assignment 1 through the browser ssh window
- Apply the following commands (Most of the commands were taken from Professor Mike Larkin's lecture. We faced few issues which we solved by taking commands from google searching, stackoverflows, chatgpt etc...)
  - cd linux/arch/x86/kvm
  - Add the necessary code logics to the two files- "cpuid.c" and "vmx/vmx.c"
  - cd ~/linux
  - make -j 16 modules
  - sudo bash
    - make INSTALL_MOD_STRIP=1 modules install && make install
    - lsmod | grep kvm
    - rmmod kvm_intel
    - rmmod kvm
    - modprobe kvm
    - lsmod | grep kvm
    - modprobe kvm_intel
    - lsmod | grep kvm
- Create a VM inside the VM we are already working with
  - This behaviour can be achieved in multiple ways. We used "chrome remote desktop"
  - Use this wonderful tutorial on how to set up Chrome Remote Desktop for Linux on Google Compute Engine: https://cloud.google.com/architecture/chrome-desktop-remote-on-compute-engine
  - Go to the terminal inside the outer virtual machine and run
    - sudo apt-get update
    - sudo apt-get install virtual-manager
    - Launch a VM using the steps given here: https://cloud.google.com/architecture/chrome-desktop-remote-on-compute-engine
- Access the virtual manager using the chrome remote desktop client
- Write test scripts
- Run test script

## Q3. Comment on the frequency of exits – does the number of exits increase at a stable rate? Or are there more exits performed during certain VM operations? Approximately how many exits does a full VM boot entail?

We can see that the exits frequencies rise steadily over time, but it does not strictly follow the linearly increasing pattern. However, we have noticed a sharp increase in the total count of exits after the virtual machine was rebooted. After a full VM boot, the frequency of exits was over 2976500.

## Q4. Of the exit types defined in the SDM, which are the most frequent? Least?

<table border="1">
  <thead>
    <tr>
      <th>Exit Number</th>
      <!-- <th>Frequency</th> -->
      <th>Exit Name</th>
      <th></th> 
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>EXIT(49)</td>
      <!-- <td>169656</td> -->
      <td>EPT_MISCONFIG</td>
      <td>Most Frequent</td>
    </tr>
    <tr>
      <td>EXIT(28)</td>
      <!-- <td>80101</td> -->
      <td>CR_ACCESS</td>
      <td>*</td>
    </tr>
    <tr>
      <td>EXIT(30)</td>
      <!-- <td>936899</td> -->
      <td>IO_INSTRUCTION</td>
      <td>*</td>
    </tr>
    <tr>
      <td>EXIT(10)</td>
      <!-- <td>42580</td> -->
      <td>CPUID</td>
      <td>*</td>
    </tr>
    <tr>
      <td>EXIT(32)</td>
      <!-- <td>11013</td> -->
      <td>MSR Access</td>
      <td>*</td>
    </tr>
     <tr>
      <td>EXIT(7)</td>
      <!-- <td>7452</td> -->
      <td>Interrupt Window</td>
      <td>*</td>
    </tr>
    <tr>
      <td>EXIT(1)</td>
      <!-- <td>10307</td> -->
      <td>External Interrupt</td>
      <td>*</td>
    </tr>
    <tr>
      <td>EXIT(48)</td>
      <!-- <td>10737</td> -->
      <td>EPT Violation</td>
      <td>*</td>
    </tr>
    <tr>
      <td>EXIT(12)</td>
      <!-- <td>3887</td> -->
      <td>HLT</td>
      <td>*</td>
    </tr>
    <tr>
      <td>EXIT(29)</td>
      <!-- <td>2</td> -->
      <td>DR_ACCESS</td>
      <td>*</td>
    </tr>
    <tr>
      <td>EXIT(0)</td>
      <!-- <td>11</td> -->
      <td>EXCEPTION_NMI</td>
      <td>*</td>
    </tr>
    <tr>
      <td>EXIT(54)</td>
      <!-- <td>6</td> -->
      <td>WBINVD</td>
      <td>Least Frequent</td>
    </tr>
  </tbody>
</table>
