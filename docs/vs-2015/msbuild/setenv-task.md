---
title: Задача SetEnv | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.setenv
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
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 49d25d49554c587bcaaba8ef09bac967d4b5599a
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59660675"
---
# <a name="setenv-task"></a>Задача SetEnv
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задает или удаляет значение указанной переменной среды.  
  
## <a name="parameters"></a>Параметры  
 В представленной ниже таблице приводятся параметры задачи **SetEnv**.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|**Name**|Обязательный параметр **string**.<br /><br /> Имя переменной среды.|  
|**OutputEnvironmentVariable**|Необязательный параметр вывода **String**.<br /><br /> Содержит значение, которое присвоено переменной среды, заданной в параметре **Name**.|  
|**Prefix**|Обязательный параметр `Boolean`.<br /><br /> Если он имеет значение `true`, значение параметра **Value** сцепляется со значением переменной среды, указанной в параметре **Name**, и результат присваивается этой переменной среды. Если `false`, переменной среды присваивается только значение **Value**.|  
|**Целевой объект**|Необязательный параметр типа **String**.<br /><br /> Задает расположение, в котором хранится переменная среды. Укажите "`User`" или "`Machine`".<br /><br /> Дополнительные сведения см. в статье "Перечисление EnvironmentVariableTarget" на веб-сайте [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
|**Значение**|Необязательный параметр типа **String**.<br /><br /> Значение, которое присваивается переменной среды, заданной в параметре **Name**. Если поле **Value** пусто, но переменная существует, то она удаляется. Если переменная не существует, ошибка не происходит, даже несмотря на невозможность выполнения операции.<br /><br /> Дополнительные сведения см. в статье "Метод Environment::SetEnvironmentVariable" на веб-сайте [MSDN](http://go.microsoft.com/fwlink/?LinkId=737).|  
  
## <a name="remarks"></a>Примечания  
  
## <a name="see-also"></a>См. также раздел  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
