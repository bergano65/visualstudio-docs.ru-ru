---
title: Задача Message | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Message
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, Message task
- Message task [MSBuild]
ms.assetid: 2293309d-42b6-46dc-9684-8c146f66bc28
caps.latest.revision: 27
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 48e867cd0993106247f7105c1102f4e1407a4fed
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59662742"
---
# <a name="message-task"></a>Задача Message
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Записывает сообщения в журнал в процессе сборки.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи `Message`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Importance`|Необязательный параметр `String` .<br /><br /> Определяет важность сообщения. Этот параметр может иметь значение `high`, `normal` или `low`. Значение по умолчанию — `normal`.|  
|`Text`|Необязательный параметр `String` .<br /><br /> Текст ошибки для записи в журнал.|  
  
## <a name="remarks"></a>Примечания  
 Задача `Message` позволяет проектам [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] отправлять сообщения в средства ведения журнал на разных этапах процесса сборки.  
  
 Если параметр `Condition` равен `true`, значение параметра `Text` записывается, а процесс сборки продолжает выполняться. Если параметр `Condition` не существует, текст сообщения записывается в журнал. Дополнительные сведения о ведении журнала см. в разделе [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 По умолчанию сообщение отправляется в средство ведения журнала консоли MSBuild. Это поведение можно изменить, присвоив параметру <xref:Microsoft.Build.Tasks.TaskExtension.Log%2A> необходимое значение. Средство ведения журнала интерпретирует параметр `Importance`.  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода сообщения регистрируются во всех зарегистрированных средствах ведения журнала.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="DisplayMessages">  
        <Message Text="Project File Name = $(MSBuildProjectFile)" />  
        <Message Text="Project Extension = $(MSBuildProjectExtension)" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md)
