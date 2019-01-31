---
title: Задача Warning | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Warning
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Warning task [MSBuild]
- MSBuild, Warning task
ms.assetid: 96ba5507-8b43-4f54-a1d7-9b15644dd56c
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 010ab0d98fa384a7b3a5d18e54a8409d5aa165b2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771925"
---
# <a name="warning-task"></a>Задача Warning
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Регистрирует в журнале предупреждение в процессе сборки на основе вычисленного условного оператора.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи `Warning`.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Code`|Необязательный параметр `String` .<br /><br /> Код предупреждения для связи с предупреждением.|  
|`File`|Необязательный параметр `String` .<br /><br /> Указывает соответствующий файл (при его наличии). Если файл не указан, используется файл, содержащий задачу Warning.|  
|`HelpKeyword`|Необязательный параметр `String` .<br /><br /> Ключевое слово справки для связи с предупреждением.|  
|`Text`|Необязательный параметр `String` .<br /><br /> Текст предупреждения, регистрируемый в журнале [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], если результат вычисления параметра `Condition` оказывается равным `true`.|  
  
## <a name="remarks"></a>Примечания  
 Задача `Warning` позволяет проектам [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] проверять наличие необходимой конфигурации или необходимого свойства перед переходом к следующему шагу сборки.  
  
 Если параметр `Condition` задачи `Warning` равен `true`, значение параметра `Text` записывается в журнал, а процесс сборки продолжается. Если параметр `Condition` не существует, текст предупреждения записывается в журнал. Дополнительные сведения о ведении журнала см. в разделе [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 Следующий пример кода проверяет свойства, заданные в командной строке. Если заданные свойства отсутствуют, проект инициирует событие предупреждения и регистрирует в журнале значение параметра `Text` задачи `Warning`.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Warning  
            Text=" The 0 property was not set on the command line."  
            Condition="'$(0)' == ''" />  
        <Warning  
            Text=" The FREEBUILD property was not set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>См. также раздел  
 [Получение журналов построения](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
