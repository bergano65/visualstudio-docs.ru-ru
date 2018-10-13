---
title: Удаление пакета VSPackage с помощью установщика Windows | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- packages, uninstalling
- VSPackages, uninstalling
- uninstalling VSPackages
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a00f2b9bd39d25510860d1d8da0484910b8991a1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283051"
---
# <a name="uninstalling-a-vspackage-with-windows-installer"></a>Удаление пакета VSPackage с помощью установщика Windows
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В большинстве случаев, установщик Windows может удалить VSPackage только по «Отмена», выполненных для установки пакета VSPackage. Пользовательские действия подробно [команды, должен быть запуска после установки](../../extensibility/internals/commands-that-must-be-run-after-installation.md) должна выполняться после удаления также. Так как вызовы devenv.exe выполнялась непосредственно перед стандартное действие функции installfinalize запущенных установок для установки и удаления, записи таблицы CustomAction и InstallExecuteSequence служат в обоих случаях.  
  
> [!NOTE]
>  Запустите `devenv /setup` после удаления пакета MSI.  
  
 Как правило при добавлении пользовательских действий в пакет установщика Windows необходимо обрабатывать эти действия во время удаления и отката. Например, при добавлении пользовательских действий для регистрации VSPackage, необходимо добавить настраиваемые действия, чтобы отменить регистрацию, слишком.  
  
> [!NOTE]
>  Возможно, пользователь может установить VSPackage и затем удалите версии [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] с которой она интегрирована. Вы можете помочь обеспечить работу удаления объекта VSPackage в этом сценарии, устраняя настраиваемых действий, выполнение кода с зависимостями на [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="handling-launch-conditions-at-uninstall-time"></a>Условия запуска обработки во время удаления  
 Стандартное действие LaunchConditions считывает строки таблицы LaunchCondition, чтобы показать ошибку сообщения, если условия не выполняются. Так как условия запуска обычно используются для убедитесь, что выполнены требования к системе, обычно можно пропустить условия запуска во время удаления, добавив условие, `NOT Installed`, преобразуется в строку в таблице LaunchCondition LaunchConditions.  
  
 Альтернативным вариантом является добавление `OR Installed` для запуска условия, которые не важны во время удаления. Это гарантирует, что условие всегда будет true во время удаления и таким образом, не будет отображаться сообщение об ошибке условие запуска.  
  
> [!NOTE]
>  `Installed` — Это свойство, которое устанавливает установщика Windows, когда обнаруживает, что VSPackage уже был установлен в системе.  
  
## <a name="see-also"></a>См. также  
 [Установщик Windows](http://msdn.microsoft.com/en-us/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)

