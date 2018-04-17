---
title: При удалении пакетов VSPackage с помощью установщика Windows | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d8a62692003b26afcd5b7814bdc03320fa1c453a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>При удалении пакетов VSPackage с помощью установщика Windows
В большинстве случаев установщик Windows может удалить VSPackage, просто «Отмена», как для установки пакета VSPackage. Пользовательские действия рассматриваются в [команды, необходимо будет запустить после установки](../../extensibility/internals/commands-that-must-be-run-after-installation.md) должен быть запущен после отмены установки. Поскольку вызовы devenv.exe возникает непосредственно перед InstallFinalize стандартного действия для установки и удаления, настраиваемое действие и InstallExecuteSequence записи таблицы используются в обоих случаях.  
  
> [!NOTE]
>  Запустите `devenv /setup` после удаления пакета MSI.  
  
 Как правило при добавлении пользовательских действий для пакета установщика Windows, необходимо обработать эти действия во время удаления и отката. Например, при добавлении пользовательских действий для регистрации VSPackage, необходимо добавить настраиваемые действия, чтобы отменить регистрацию, слишком.  
  
> [!NOTE]
>  Возможно, пользователь может установить VSPackage и затем удалите версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с которой интегрирован. Чтобы обеспечить работоспособность удаления вашего VSPackage в этом сценарии, устраняя пользовательские действия, выполнение кода с зависимостями на [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Условия запуска обработки во время установки  
 Стандартное действие LaunchConditions считывает строки таблицы для отображения ошибки LaunchCondition сообщений, если условия не выполняются. Как условия запуска обычно используются, чтобы убедиться, что выполнены требования к системе, обычно можно пропустить условия запуска в процессе удаления, добавив условие, `NOT Installed`, в строку LaunchConditions LaunchCondition таблицы.  
  
 Альтернативным вариантом является добавление `OR Installed` для запуска условия, которые не представляют интереса в процессе удаления. Это гарантирует, что условие всегда будет значение true во время удаления и таким образом, не будет отображаться сообщение об ошибке условие запуска.  
  
> [!NOTE]
>  `Installed` Представляет свойство, которое устанавливает установщика Windows, когда обнаруживает, что VSPackage уже был установлен в системе.  
  
## <a name="see-also"></a>См. также  
 [Установщик Windows](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)