---
title: "Отладчик контексты | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f36df39cf29ff298a327ec6e6d4bb02ff53485a0
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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