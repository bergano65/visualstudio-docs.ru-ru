---
title: "Практическое руководство. Игнорирование ошибок в задачах | Документы Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
caps.latest.revision: 18
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 3ba7680d46345f2b49019659c715cfb418933d39
ms.openlocfilehash: 263a2cdc87b46a70d9114a830955a54cde85d527
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-ignore-errors-in-tasks"></a>Практическое руководство. Игнорирование ошибок в задачах
Иногда требуется, чтобы сборка была отказоустойчивой при выполнении определенных задач. В случае появления ошибки в таких некритических задачах сборку можно продолжить, поскольку это не помешает получить требуемый результат. Например, если в проекте используется задача `SendMail` для отправки сообщения электронной почты после сборки каждого компонента, вы можете пожелать продолжить сборку до полного завершения даже в том случае, если почтовые серверы оказываются недоступными и не удается отправить сообщения о состоянии. Или, например, если промежуточные файлы обычно удаляются во время сборки, вы можете пожелать продолжить выполнение сборки до полного завершения даже в том случае, если эти файлы не удается удалить.  
  
## <a name="using-the-continueonerror-attribute"></a>Использование атрибута ContinueOnError  
 Атрибут `ContinueOnError` элемента `Task` определяет, следует ли остановить или продолжить сборку в случае, если в задаче произошла ошибка. Этот атрибут также контролирует, обрабатываются ли ошибки в виде ошибки или предупреждения, когда сборка продолжается.  
  
 Атрибут `ContinueOnError` может содержать одно из следующих значений:  
  
-   **WarnAndContinue** или **true**. При сбое задачи последующие задачи в элементе [Target](../msbuild/target-element-msbuild.md) и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как предупреждения.  
  
-   **ErrorAndContinue**. При сбое задачи последующие задачи в элементе `Target` и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как ошибки.  
  
-   **ErrorAndStop** или **false** (по умолчанию). При сбое задачи остальные задачи в элементе `Target` и сборке не выполняются, и считается, что возник сбой всего элемента `Target` и всей сборки.  
  
 Версии платформы .NET Framework, предшествовавшие 4.5, поддерживали только значения `true` и `false`.  
  
 Значением свойства `ContinueOnError` по умолчанию является `ErrorAndStop`. Если задать для атрибута значение `ErrorAndStop`, можно сделать такое поведение явным для всех объектов, считывающих файл проекта.  
  
#### <a name="to-ignore-an-error-in-a-task"></a>Игнорирование ошибки в задаче  
  
-   Используйте атрибут `ContinueOnError` задачи. Пример:  
  
     `<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>`  
  
## <a name="example"></a>Пример  
 В следующем примере кода показано, что целевой объект `Build` по-прежнему выполняется, а сборка считается успешной, даже если задача `Delete` завершается с ошибкой.  
  
```xml  
<Project DefaultTargets="FakeBuild"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <ItemGroup>  
        <Files Include="*.obj"/>  
    </ItemGroup>  
    <Target Name="Clean">  
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>  
    </Target>  
  
    <Target Name="FakeBuild" DependsOnTargets="Clean">  
        <Message Text="Building after cleaning..."/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>См. также
[MSBuild](../msbuild/msbuild.md)  
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Задачи](../msbuild/msbuild-tasks.md)
