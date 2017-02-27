---
title: "Задача SetEnv | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.task.setenv"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
  - "C++"
helpviewer_keywords: 
  - "MSBuild (Visual C++), задачи"
  - "SetEnv - задача (MSBuild (Visual C++))"
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Задача SetEnv
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задает или удаляет значение указанной переменной среды.  
  
## Параметры  
 В следующей таблице описаны параметры задачи **SetEnv** .  
  
|Параметр|Описание|  
|--------------|--------------|  
|**Name**|Обязательный параметр типа **String**.<br /><br /> Имя переменной среды.|  
|**OutputEnvironmentVariable**|Необязательный выходной параметр **String**.<br /><br /> Содержит значение, которое назначено переменной среды, заданной параметром **Name**.|  
|**Prefix**|Обязательный параметр `Boolean`.<br /><br /> Если он имеет значение `true`, то значение параметра **Value** прикрепляется перед значением переменной среды, указанной в параметре **Name**, и результат назначается этой переменной среды.  Если `false`, то этой переменной среды назначается только значение **Value**.|  
|**Target**|Необязательный параметр типа **String**.<br /><br /> Задает расположение, в котором хранится переменная среды.  Укажите "`Пользователь`" или "`Компьютер`".<br /><br /> Дополнительные сведения см. в статье "Перечисление EnvironmentVariableTarget" на веб\-сайте [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**Value**|Необязательный параметр типа **String**.<br /><br /> Значение, которое назначено переменной среды, заданной параметром **Name**.  Если поле **Value** пусто, но переменная существует, то эта переменная удаляется.  Если переменная не существует, ошибка не происходит, даже не смотря на невозможность выполнения операции.<br /><br /> Дополнительные сведения см. в статье "Метод Environment::SetEnvironmentVariable" на веб\-сайте [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## Заметки  
  
## См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)