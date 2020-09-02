---
title: Удаление VSPackage с установщик Windows | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 9a309779850dd33b77b426beb5627f61c40c2c4f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675233"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Удаление пакета VSPackage с помощью установщика Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В большинстве случаев установщик Windows может удалить пакет VSPackage, просто отменив его, чтобы установить пакет VSPackage. Пользовательские действия, описанные в [командах, которые должны быть выполнены после установки,](../../extensibility/internals/commands-that-must-be-run-after-installation.md) должны быть выполнены и после удаления. Поскольку вызовы devenv.exe происходят непосредственно перед стандартным действием функции InstallFinalize как для установки, так и для удаления, записи в таблице CustomAction и Инсталлексекутесекуенце служат обоим случаям.  
  
> [!NOTE]
> Запустите `devenv /setup` после удаления пакета MSI.  
  
 Как правило, при добавлении настраиваемых действий в пакет установщик Windows необходимо выполнять эти действия во время удаления и отката. При добавлении настраиваемых действий для самостоятельной регистрации пакета VSPackage, например, необходимо добавить настраиваемые действия, чтобы отменить его регистрацию.  
  
> [!NOTE]
> Пользователь может установить пакет VSPackage, а затем удалить версии, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] с которыми он интегрируется. Чтобы убедиться в том, что удаление VSPackage работает в этом сценарии, следует исключить пользовательские действия, которые выполняют код с зависимостями [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Обработка условий запуска во время удаления  
 Стандартное действие Лаунчкондитионс считывает строки таблицы Лаунчкондитион для отображения сообщений об ошибках, если условия не выполнены. Поскольку условия запуска обычно используются для обеспечения соответствия требованиям к системе, обычно можно пропустить условия запуска во время удаления, добавив условие, `NOT Installed` в строку лаунчкондитионс таблицы лаунчкондитион.  
  
 Альтернативой является добавление `OR Installed` в условия запуска, которые не важны во время удаления. Это гарантирует, что условие будет всегда истинно во время удаления, и поэтому не отобразит сообщение об ошибке условия запуска.  
  
> [!NOTE]
> `Installed` Свойство установщик Windows задается при обнаружении того, что пакет VSPackage уже установлен в системе.  
  
## <a name="see-also"></a>См. также:  
 [установщик Windows](https://msdn.microsoft.com/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)
