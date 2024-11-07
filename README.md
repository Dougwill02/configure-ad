# configure-ad


<h2>Environments and Technologies Used</h2>
<ul>
    <li>Microsoft Azure (Virtual Machines/Compute)</li>
    <li>Remote Desktop</li>
    <li>Active Directory Domain Services</li>
    <li>PowerShell</li>
</ul>

<h2>Operating Systems Used</h2>
<ul>
    <li>Windows Server 2022</li>
    <li>Windows 10 (21H2)</li>
</ul>

<h2>High-Level Deployment and Configuration Steps</h2>
<ul>
    <li>Step 1: Set up Virtual Machines in Azure</li>
    <li>Step 2: Install Active Directory Domain Services (AD DS)</li>
    <li>Step 3: Configure Active Directory and Domain Controllers</li>
    <li>Step 4: Join Azure-based machines to the domain</li>
</ul>

<h2>Deployment and Configuration Steps</h2>

<h3>1. Set up Virtual Machines in Azure</h3>
<p>The first step is to deploy a Virtual Machine (VM) in Azure that will host your on-premises Active Directory Domain Services (AD DS). This can be done using Azure’s Virtual Machines service. The VM should meet the minimum requirements for Active Directory installation.</p>
<ul>
    <li>Navigate to the Azure portal and create a new VM, selecting Windows Server 2022 as the operating system.</li>
    <li>Ensure the VM has sufficient CPU, memory, and storage resources to handle Active Directory Domain Services.</li>
    <li>Assign a static IP to the VM to ensure stable connectivity during configuration.</li>
    <li>Configure Remote Desktop access to the VM for administrative tasks.</li>
</ul>

<h3>2. Install Active Directory Domain Services (AD DS)</h3>
<p>Once the Virtual Machine is set up and accessible, the next step is to install Active Directory Domain Services. This process involves installing the required roles and features on the Windows Server.</p>
<ul>
    <li>Open the Server Manager on the Windows Server VM.</li>
    <li>Select "Add roles and features" and proceed through the wizard to install the "Active Directory Domain Services" role.</li>
    <li>After installation, you will be prompted to promote the server to a Domain Controller (DC). Follow the steps to configure your domain.</li>
</ul>

<h3>3. Configure Active Directory and Domain Controllers</h3>
<p>After installing AD DS, you will need to configure Active Directory and set up a domain controller (DC) for your environment.</p>
<ul>
    <li>Run the Active Directory Domain Services Configuration Wizard from the Server Manager.</li>
    <li>Create a new forest or join an existing domain, depending on your use case.</li>
    <li>Specify a domain name (e.g., example.com) and configure DNS settings.</li>
    <li>Set the Directory Services Restore Mode (DSRM) password and complete the installation. This will configure the server as your first domain controller in the new AD forest.</li>
    <li>Once completed, the server will automatically restart, and Active Directory will be fully configured.</li>
</ul>

<h3>4. Join Azure-based Machines to the Domain</h3>
<p>Now that the Active Directory domain is set up, you can join additional Azure-based Virtual Machines to the domain. This allows you to extend the on-premises Active Directory services to your cloud-based infrastructure.</p>
<ul>
    <li>On the target Azure VM (running Windows 10 or another server), open System Properties and navigate to the "Computer Name" tab.</li>
    <li>Click "Change" to join the machine to the domain created earlier.</li>
    <li>Enter the domain name and provide credentials of an account with permissions to join the domain (usually a Domain Administrator).</li>
    <li>Once joined, restart the VM for the changes to take effect. You can now log in to the Azure VM using Active Directory credentials.</li>
</ul>
