# Day-17

### ✅ **Prerequisites**

1. **Install Terraform**: [Download Terraform](https://developer.hashicorp.com/terraform/downloads)
2. **Azure CLI installed**: [Install Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)
3. **Azure account**: [Sign up or log in](https://portal.azure.com)
4. **Login to Azure**:

   ```bash
   az login
   ```

---

### 📁 **Project Structure**

Create a folder and inside it, make a file named `main.tf`.

```
azure_vm/
│
└── main.tf
```

---

### 🛠️ **Step-by-step Terraform Code (`main.tf`)**

```hcl
provider "azurerm" {
  features {}
}

resource "azurerm_resource_group" "rg" {
  name     = "myResourceGroup"
  location = "East US"
}

resource "azurerm_virtual_network" "vnet" {
  name                = "myVNet"
  address_space       = ["10.0.0.0/16"]
  location            = azurerm_resource_group.rg.location
  resource_group_name = azurerm_resource_group.rg.name
}

resource "azurerm_subnet" "subnet" {
  name                 = "mySubnet"
  resource_group_name  = azurerm_resource_group.rg.name
  virtual_network_name = azurerm_virtual_network.vnet.name
  address_prefixes     = ["10.0.1.0/24"]
}

resource "azurerm_network_interface" "nic" {
  name                = "myNIC"
  location            = azurerm_resource_group.rg.location
  resource_group_name = azurerm_resource_group.rg.name

  ip_configuration {
    name                          = "internal"
    subnet_id                    = azurerm_subnet.subnet.id
    private_ip_address_allocation = "Dynamic"
  }
}

resource "azurerm_windows_virtual_machine" "vm" {
  name                  = "myVM"
  location              = azurerm_resource_group.rg.location
  resource_group_name   = azurerm_resource_group.rg.name
  network_interface_ids = [azurerm_network_interface.nic.id]
  size                  = "Standard_DS1_v2"
  admin_username        = "adminuser"
  admin_password        = "Password1234!"  # Make this secure in real environments

  os_disk {
    caching              = "ReadWrite"
    storage_account_type = "Standard_LRS"
  }

  source_image_reference {
    publisher = "MicrosoftWindowsServer"
    offer     = "WindowsServer"
    sku       = "2019-Datacenter"
    version   = "latest"
  }
}
```

---

### ⚙️ **Commands to Run**

1. **Initialize the directory**:

   ```bash
   terraform init
   ```

2. **Review the plan**:

   ```bash
   terraform plan
   ```

3. **Apply the configuration**:

   ```bash
   terraform apply
   ```

4. **Confirm when prompted (`yes`)**

---

### 🧹 To Destroy the Resources

```bash
terraform destroy
```

---

### 📌 Notes

* For a **Linux VM**, use `azurerm_linux_virtual_machine` and update the `source_image_reference`.
* You can also use variables (`variables.tf`) and outputs (`outputs.tf`) to make the setup more modular.


![Uploading ChatGPT Image Jun 5, 2025, 05_04_25 PM.png…]()


