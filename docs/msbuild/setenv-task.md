---
title: "Задача SetEnv | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.task.setenv
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- SetEnv task (MSBuild (Visual C++))
ms.assetid: fd9e4225-68cb-4608-8b27-468b0218c936
caps.latest.revision: "6"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 0223d57cf4c16166149b1fc9e8903f563b724d20
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="setenv-task"></a>Задача SetEnv
Задает или удаляет значение указанной переменной среды.  
  
## <a name="parameters"></a>Параметры  
 В представленной ниже таблице приводятся параметры задачи **SetEnv**.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|**Имя**|Обязательный параметр **string**.<br /><br /> Имя переменной среды.|  
|**OutputEnvironmentVariable**|Необязательный параметр вывода **String**.<br /><br /> Содержит значение, которое присвоено переменной среды, заданной в параметре **Name**.|  
|**Prefix**|Обязательный параметр `Boolean`.<br /><br /> Если он имеет значение `true`, значение параметра **Value** сцепляется со значением переменной среды, указанной в параметре **Name**, и результат присваивается этой переменной среды. Если `false`, переменной среды присваивается только значение **Value**.|  
|**Целевой объект**|Необязательный параметр типа **String**.<br /><br /> Задает расположение, в котором хранится переменная среды. Укажите "`User`" или "`Machine`".<br /><br /> Дополнительные сведения см. в статье "Перечисление EnvironmentVariableTarget" на веб-сайте [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**Значение**|Необязательный параметр типа **String**.<br /><br /> Значение, которое присваивается переменной среды, заданной в параметре **Name**. Если поле **Value** пусто, но переменная существует, то она удаляется. Если переменная не существует, ошибка не происходит, даже несмотря на невозможность выполнения операции.<br /><br /> Дополнительные сведения см. в статье "Метод Environment::SetEnvironmentVariable" на веб-сайте [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)