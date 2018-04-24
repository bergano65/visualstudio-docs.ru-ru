---
title: Задача Error | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Error
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Error task [MSBuild]
- MSBuild, Error task
ms.assetid: e96a90ee-a8ae-4e5b-8ef2-b5cf5fedd8b2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0f43f585320c34da17948e30d2672de9c9aa51e4
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="error-task"></a>Задача Error
Останавливает сборку и регистрирует ошибку в журнале событий на основании вычисленного условного оператора.  
  
## <a name="parameters"></a>Параметры  
 В следующей таблице описаны параметры задачи `Error`.  
  
|Параметр|Описание:|  
|---------------|-----------------|  
|`Code`|Необязательный параметр `String` .<br /><br /> Код ошибки для связи с ошибкой.|  
|`File`|Необязательный параметр `String` .<br /><br /> Имя файла, содержащего ошибку. Если имя файла не указано, используется файл, содержащий задачу Error.|  
|`HelpKeyword`|Необязательный параметр `String` .<br /><br /> Ключевое слово справки, связанное с ошибкой.|  
|`Text`|Необязательный параметр `String` .<br /><br /> Текст ошибки, регистрируемый в журнале [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], если результат вычисления параметра `Condition` оказывается равным `true`.|  
  
## <a name="remarks"></a>Примечания  
 Задача `Error` позволяет передавать текст ошибок в средства ведения журнала и останавливать выполнение сборки в проектах [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 Если результат вычисления параметра `Condition` оказывается равным `true`, сборка останавливается, а ошибка регистрируется в журнале. Если параметр `Condition` не существует, ошибка регистрируется в журнале, а выполнение сборки останавливается. Дополнительные сведения о ведении журнала см. в разделе [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md).  
  
 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [TaskExtension Base Class](../msbuild/taskextension-base-class.md).  
  
## <a name="example"></a>Пример  
 В следующем примере кода проверяется, что установлены все обязательные свойства. Если это не так, проект инициирует событие ошибки и регистрирует в журнале значение параметра `Text` задачи `Error`.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="ValidateCommandLine">  
        <Error  
            Text=" The 0 property must be set on the command line."  
            Condition="'$(0)' == ''" />  
        <Error  
            Text="The FREEBUILD property must be set on the command line."  
            Condition="'$(FREEBUILD)' == ''" />  
    </Target>  
    ...  
</Project>  
```  
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md)