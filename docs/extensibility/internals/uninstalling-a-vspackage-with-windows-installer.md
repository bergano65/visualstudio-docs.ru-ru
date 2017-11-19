---
title: "При удалении пакетов VSPackage с помощью установщика Windows | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9b71c977fcc616c6d9cf30b78c9fd7610f11bcd4
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
>  `Installed`Представляет свойство, которое устанавливает установщика Windows, когда обнаруживает, что VSPackage уже был установлен в системе.  
  
## <a name="see-also"></a>См. также  
 [Установщик Windows](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)