# Windows Lockscreen Program

## Description
This project is a C# application developed in Visual Studio that runs directly on the Windows lock screen. It provides functionality that enhances the lock screen experience. The application requires setting up a certificate snap-in for proper functionality and importing/exporting a provided certificate (`Certificate.pfx`).

## Table of Contents
- [Requirements](#requirements)
- [Installation](#installation)
  - [Step 1: Create a Certificate Snap-In](#step-1-create-a-certificate-snap-in)
  - [Step 2: Import, Export, and Re-Import the Certificate](#step-2-import-export-and-re-import-the-certificate)
  - [Step 3: Copy the Executable File](#step-3-copy-the-executable-file)
- [Running the Application](#running-the-application)
- [Features](#features)
- [Contributing](#contributing)
- [License](#license)

## Requirements
- **Windows Operating System**
- **Visual Studio** (for any further development)
- **C# Runtime Environment**
- **Certificate.pfx** file (provided with the project)

## Installation

### Step 1: Create a Certificate Snap-In
To ensure the application runs properly on the Windows lock screen, a certificate snap-in must be created:

1. Press `Win + R` to open the Run dialog, type `mmc`, and press Enter.
2. In the Microsoft Management Console (MMC):
   - Go to the menu and select **File > Add/Remove Snap-in**.
3. From the list of available snap-ins:
   - Select **Certificates** and click **Add**.
4. When prompted, select **Computer account**, then click **Next**.
5. Choose **Local Computer** and click **Finish**.
6. Click **OK** to return to the main MMC window.

Now you have configured a snap-in to manage certificates on your computer.

---

### Step 2: Import, Export, and Re-Import the Certificate
To complete the setup, you will use the provided `Certificate.pfx` file and ensure it is imported into the correct certificate stores.

#### **Part 1: Import the Certificate into Personal/Certificates**
1. In the MMC window, expand **Certificates (Local Computer)** and navigate to **Personal > Certificates**.
2. Right-click **Certificates** under **Personal**, and select **All Tasks > Import**.
3. In the Import Wizard:
   - Click **Next** and browse to the `Certificate.pfx` file.
   - Enter the password (if required) for the `.pfx` file, and ensure the option **Mark this key as exportable** is checked.
   - Continue through the wizard and select the **Personal** store as the destination.
   - Finish the import process.

#### **Part 2: Export the Certificate**
1. Locate the certificate you just imported under **Personal > Certificates**.
2. Right-click the certificate, select **All Tasks > Export**, and follow these steps in the Export Wizard:
   - Choose **Yes, export the private key** and click **Next**.
   - Select the default format or **PFX**, and include all certificates in the certification path.
   - Set a password if prompted.
   - Save the exported file in a secure location (e.g., `Certificate_Exported.pfx`).

#### **Part 3: Re-Import the Certificate to Trusted Root Certification Authorities**
1. Expand **Trusted Root Certification Authorities > Certificates**.
2. Right-click **Certificates** and select **All Tasks > Import**.
3. Import the `Certificate_Exported.pfx` file you exported earlier.
4. Complete the wizard to add the certificate to the **Trusted Root Certification Authorities** store.

---

### Step 3: Copy the Executable File
1. Build the project in Visual Studio to generate the `.exe` file.
2. Navigate to the output directory (e.g., `bin\Release` or `bin\Debug`) to locate the `.exe` file.
3. Copy the `.exe` file to the following directory:
   ```plaintext
   C:\programs
