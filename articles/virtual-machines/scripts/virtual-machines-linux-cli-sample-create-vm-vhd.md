---
title: Azure CLI Script Sample - Create a VM with a VHD  | Microsoft Docs
description: Azure CLI Script Sample - Create a VM using a virtual hard disk.
services: virtual-machines-linux
documentationcenter: virtual-machines
author: allclark
manager: douge
editor: tysonn
tags: azure-service-management

ms.assetid:
ms.service: virtual-machines-linux
ms.devlang: na
ms.topic: article
ms.tgt_pltfrm: vm-linux
ms.workload: infrastructure
ms.date: 03/06/2017
ms.author: allclark
---

# Create a VM with a virtual hard disk

This example creates a virtual machine using a VHD.
It creates a resource group, a storage account, and a container,
then it creates a VM by uploading the VHD to the container.
It replaces the ssh public key with your public key so that you have access to the VM.

You'll need a bootable VHD.
You can download the VHD that we used from https://azclisamples.blob.core.windows.net/vhds/sample.vhd,
or use your own VHD. The script looks for `~/sample.vhd`.

This sample works in a Bash shell. For options on running Azure CLI scripts on Windows client, see [Running the Azure CLI in Windows](../virtual-machines-windows-cli-options.md).

## Sample script

[!code-azurecli[main](../../../cli_scripts/virtual-machine/create-vm-vhd/create-vm-vhd.sh "Create VM using a VHD")]

## Clean up deployment 

After the script sample has been run, the following command can be used to remove the resource groups, VMs, and all related resources.

```azurecli
az group delete -n az-cli-vhd
```

## Script explanation

This script uses the following commands to create a resource group, virtual machine, availability set, load balancer, and all related resources. Each command in the table links to command specific documentation.

| Command | Notes |
|---|---|
| [az group create](https://docs.microsoft.com/cli/azure/group#create) | Creates a resource group in which all resources are stored. |
| [az storage account list](https://docs.microsoft.com/cli/azure/storage/account#list) | Lists storage accounts |
| [az storage account check-name](https://docs.microsoft.com/cli/azure/storage/account#check-name) | Checks that a storage account name is valid and that it doesn't already exist |
| [az storage account keys list](https://docs.microsoft.com/cli/azure/storage/account/keys#list) | Lists keys for the storage accounts |
| [az storage blob exists](https://docs.microsoft.com/cli/azure/storage/blob#exists) | Checks whether the blob exists |
| [az storage container create](https://docs.microsoft.com/cli/azure/storage/container#create) | Creates a container in a storage account. |
| [az storage blob upload](https://docs.microsoft.com/cli/azure/storage/blob#upload) | Creates a blob in the container by uploading the VHD. |
| [az vm list](https://docs.microsoft.com/cli/azure/vm#list) | Used with `--query` check whether the VM name is in use. | 
| [az vm create](https://docs.microsoft.com/cli/azure/vm/availability-set#create) | Creates the virtual machines. |
| [az vm access set-linux-user](https://docs.microsoft.com/cli/azure/vm/access#set-linux-user) | Resets the SSH key to give the current user access to the VM. |
| [az vm list-ip-addresses](https://docs.microsoft.com/cli/azure/vm#list-ip-addresses) | Gets the IP address of the VM that was created. |

## Next steps

For more information on the Azure CLI, see [Azure CLI documentation](https://docs.microsoft.com/cli/azure/overview).

Additional virtual machine CLI script samples can be found in the [Azure Linux VM documentation](../virtual-machines-linux-cli-samples.md?toc=%2fazure%2fvirtual-machines%2flinux%2ftoc.json).
