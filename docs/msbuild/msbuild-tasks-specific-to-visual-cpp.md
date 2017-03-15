---
title: "Задачи MSBuild, относящиеся к Visual C++ | Документация Майкрософт"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 7
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d82c6e70e17866e4bd4d39524faafdb554508fc2
ms.lasthandoff: 02/22/2017

---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Задачи MSBuild, относящиеся к Visual C++
Задачи содержат код, который выполняется в процессе сборки. После установки Visual C++ доступны следующие задачи, помимо тех, которые устанавливаются вместе с [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Дополнительные сведения см. в [обзоре MSBuild (Visual C++)](/visual-cpp/build/msbuild-visual-cpp-overview).  
  
 Помимо общих для всех задач параметров, у каждой задачи есть следующие параметры.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Condition`|Необязательный параметр `String` .<br /><br /> Выражение `Boolean`, на основании которого механизм [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] определяет, будет ли выполняться эта задача. Сведения о поддерживаемых в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] условиях см. в статье [об условиях MSBuild](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Необязательный параметр. Может содержать одно из следующих значений:<br /><br /> -   **WarnAndContinue** или **true**. При сбое одной задачи продолжается выполнение сборки и всех последующих задач в элементе [Target](../msbuild/target-element-msbuild.md), а все ошибки из задачи рассматриваются как предупреждения.<br />-   **ErrorAndContinue**. При сбое задачи последующие задачи в элементе `Target` и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как ошибки.<br />-   **ErrorAndStop** или **false** (значение по умолчанию). При сбое задачи отменяется выполнение сборки и последующих задач в элементе `Target`, и фиксируется сбой для выполнения элемента `Target` и всей сборки.<br /><br /> Версии платформы .NET Framework, предшествовавшие 4.5, поддерживали только значения `true` и `false`.<br /><br /> Дополнительные сведения см. в статье [Практическое руководство. Игнорирование ошибок в задачах](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>Связанные разделы  
  
|Заголовок|Описание|  
|-----------|-----------------|  
|[Задача BscMake](../msbuild/bscmake-task.md)|Заключает в оболочку средство «Программа управления сведениями о просмотре Майкрософт» (bscmake.exe).|  
|[Задача CL](../msbuild/cl-task.md)|Является оболочкой для средства компиляции Visual C++ (cl.exe).|  
|[Задача CPPClean](../msbuild/cppclean-task.md)|Удаляет временные файлы, которые MSBuild создает при сборке проекта Visual C++.|  
|[Задача LIB](../msbuild/lib-task.md)|Является оболочкой для 32-разрядного диспетчера библиотек Microsoft (lib.exe).|  
|[Связывание задачи](../msbuild/link-task.md)|Является оболочкой для компоновщика Visual C++ (link.exe).|  
|[Задача MIDL](../msbuild/midl-task.md)|Является оболочкой для компилятора с языка MIDL (midl.exe).|  
|[Задача MT](../msbuild/mt-task.md)|Является оболочкой для инструмента манифеста Microsoft (mt.exe).|  
|[Задача RC](../msbuild/rc-task.md)|Является оболочкой для средства компиляции ресурсов Microsoft Windows (rc.exe).|  
|[Задача SetEnv](../msbuild/setenv-task.md)|Задает или удаляет значение указанной переменной среды.|  
|[Задача VCMessage](../msbuild/vcmessage-task.md)|Заносит в журнал предупреждения и сообщения об ошибках, возникшие при сборке.|  
|[Задача XDCMake](../msbuild/xdcmake-task.md)|Является оболочкой для средства XML-документации (xdcmake.exe), которая помещает в XML-файл файлы комментариев (XDC-файлы) для документа XML.|  
|[Задача XSD](../msbuild/xsd-task.md)|Создает оболочку инструмента определения схемы XML (xsd.exe), который создает файлы схемы или класса из источника.|  
|[Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)|Описывает элементы системы MSBuild.|  
|[Задачи](../msbuild/msbuild-tasks.md)|Описывает задачи, представляющие собой блоки кода, которые можно объединять для выполнения сборки.|  
|[Написание задач](../msbuild/task-writing.md)|Создание задачи.|
