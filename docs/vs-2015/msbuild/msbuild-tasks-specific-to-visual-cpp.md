---
title: Задачи MSBuild, относящиеся к Visual C++ | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4f4de01af6535a33607e5263966492210f8ce4a5
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647967"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Задачи MSBuild, относящиеся к Visual C++
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Задачи содержат код, который выполняется в процессе сборки. После установки Visual C++ доступны следующие задачи, помимо тех, которые устанавливаются вместе с [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Дополнительные сведения см. в [обзоре MSBuild (Visual C++)](http://msdn.microsoft.com/library/dd258f6f-ab51-48d9-b274-f7ba911d05ca).  
  
 Помимо общих для всех задач параметров, у каждой задачи есть следующие параметры.  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`Condition`|Необязательный параметр `String` .<br /><br /> Выражение `Boolean`, на основании которого механизм [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] определяет, будет ли выполняться эта задача. Сведения о поддерживаемых в [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] условиях см. в статье [об условиях MSBuild](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|Необязательный параметр. Может содержать одно из следующих значений:<br /><br /> -   **WarnAndContinue** или **true**. При сбое одной задачи продолжается выполнение сборки и всех последующих задач в элементе [Target](../msbuild/target-element-msbuild.md), а все ошибки из задачи рассматриваются как предупреждения.<br />-   **ErrorAndContinue**. При сбое задачи последующие задачи в элементе `Target` и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как ошибки.<br />-   **ErrorAndStop** или **false** (значение по умолчанию). При сбое задачи отменяется выполнение сборки и последующих задач в элементе `Target`, и фиксируется сбой для выполнения элемента `Target` и всей сборки.<br /><br /> Версии платформы .NET Framework, предшествовавшие 4.5, поддерживали только значения `true` и `false`.<br /><br /> Дополнительные сведения см. в разделе [Как Игнорирование ошибок в задачах](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>См. также  
  
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
