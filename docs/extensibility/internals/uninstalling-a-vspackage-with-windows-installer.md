---
title: "При удалении VSPackage с помощью установщика Windows | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "удаление пакетов"
  - "Пакеты VSPackage, удаление"
  - "При удалении пакетов VSPackage"
ms.assetid: c4575ac7-82da-4af8-a375-ea756a101fbf
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# При удалении VSPackage с помощью установщика Windows
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

В большинстве случаев установщик Windows может удалить VSPackage, просто «Отмена», как установка VSPackage. Настраиваемые действия подробно [Команды, которые необходимо выполнить после установки](../../extensibility/internals/commands-that-must-be-run-after-installation.md) должна выполняться после отмены установки. Поскольку вызовы devenv.exe возникает непосредственно перед стандартное действие функции installfinalize установок для установки и удаления, CustomAction и InstallExecuteSequence записи таблицы служат в обоих случаях.  
  
> [!NOTE]
>  Запустить `devenv /setup` после удаления пакета MSI.  
  
 Как правило при добавлении настраиваемых действий в пакет установщика Windows должен обрабатывать эти действия во время удаления и отката. Например, при добавлении настраиваемых действий для регистрации VSPackage, необходимо добавить настраиваемые действия, чтобы отменить регистрацию, слишком.  
  
> [!NOTE]
>  Возможно, пользователь может установить VSPackage, а затем удалите версии [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] с которой она интегрирована. Это поможет убедиться, что ваш VSPackage удаления работает в этом сценарии, устраняя особых действий, выполняемых в коде с зависимостями [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Условия запуска обработки во время удаления  
 Стандартное действие LaunchConditions считывает строки таблицы для отображения ошибки LaunchCondition сообщений, если условия не выполняются. Чтобы убедиться, что соблюдены требования к системе, обычно можно пропустить условия запуска во время удаления, добавив условие, обычно используются условия запуска `NOT Installed`, LaunchConditions строке в таблице LaunchCondition.  
  
 Альтернативным вариантом является добавление `OR Installed` для запуска условия, которые не важны во время удаления. Это гарантирует, что условие всегда будет значение true во время удаления и таким образом не отобразит сообщение об ошибке условие запуска.  
  
> [!NOTE]
>  `Installed` Представляет свойство, которое устанавливает установщика Windows, когда обнаруживает, что VSPackage уже установлены в системе.  
  
## См. также  
 [Windows Installer](http://msdn.microsoft.com/ru-ru/187d8965-c79d-4ecb-8689-10930fa8b3b5)   
 [Определение требований к системе](../../extensibility/internals/detecting-system-requirements.md)