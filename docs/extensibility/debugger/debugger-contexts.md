---
title: Отладчик контексты | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8a9310512417ac0e24046a1b7bcc1fd92099fe98
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31099422"
---
# <a name="debugger-contexts"></a>Контексты отладчика
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладки, отладчик (DE) работает одновременно в нескольких различных контекстах, следующим образом:  
  
-   Контекст кода, который описывает текущее расположение в поток выполнения программы.  
  
-   Контекст документации или положение, описывающий текущую позицию в исходном документе.  
  
-   Контекст оценки выражения, который описывает контекст, в которой выражение будет вычислить.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Контекст кода](../../extensibility/debugger/code-context.md)  
 Описывает контекст кода как адрес в поток инструкций программы в архитектурах во время выполнения по текущей и нетрадиционных языков, где код не представлены инструкции, но другие средства.  
  
 [Позиция в документе](../../extensibility/debugger/document-position.md)  
 Определяет позицию в документе при отладке Visual Studio с помощью абстракцию позиции в файле исходного кода, как оно известно в Интегрированной среде разработки.  
  
 [Контекст документа](../../extensibility/debugger/document-context.md)  
 Описывает представляет какой контекст документа в Visual Studio, отладка относительно исходного файла. Также описывается, как обработчик символов сопоставляет контекст кода контекста документацией.  
  
 [Контекст вычисления выражений](../../extensibility/debugger/expression-evaluation-context.md)  
 Сведения о контексте вычисления выражения в Visual Studio. Например контекст оценки выражения, связанный с кадром стека предоставляет контекст для оценки локальных переменных, параметров метода и членов класса.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Основные понятия отладки](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные принципы отладки архитектуры.  
  
 [Компоненты отладки](../../extensibility/debugger/debugger-components.md)  
 Общие компоненты отладки Visual Studio, которые включают модуль отладки (DE), средство оценки выражений (EE) и обработчик символ (SH).  
  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, например, запустив программу и оценки выражений.