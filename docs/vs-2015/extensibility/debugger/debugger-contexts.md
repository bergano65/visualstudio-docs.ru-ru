---
title: Контексты отладчика | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4227bd8a82df031f04c1ab33761cf9b8520dec7a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991543"
---
# <a name="debugger-contexts"></a>Контексты отладчика
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

В [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] отладки, отладчик (DE) работает одновременно в нескольких разных контекстах, следующим образом:  
  
-   Контекст кода, который описывает текущее расположение в потоке выполнения программы.  
  
-   Документация по контекста или позиции, описывающий текущую позицию внутри документа с исходным.  
  
-   Контекст вычисления выражения, который описывает контекст, в вычисление какого выражения вычислений будет иметь место.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Контекст кода](../../extensibility/debugger/code-context.md)  
 Контекст кода рассматриваются как адреса в потоке инструкций программы в архитектурах времени выполнения по современных и нетрадиционных языков, где код не представлены инструкции, но либо иным образом.  
  
 [Позиция в документе](../../extensibility/debugger/document-position.md)  
 Определяет положение документа в Visual Studio, отладка посредством абстракции для положения в исходном файле, известная интегрированной среды разработки.  
  
 [Контекст документа](../../extensibility/debugger/document-context.md)  
 Описывает контекст документа представляет в Visual Studio, отладка по отношению к исходным файлом. Также обсуждается, как обработчик символ сопоставляет контекст кода контекста документации.  
  
 [Контекст вычисления выражений](../../extensibility/debugger/expression-evaluation-context.md)  
 Сведения о контексте вычисления выражения в Visual Studio. Например контекст вычисления выражения, связанный с кадром стека предоставляет контекст для оценки локальных переменных, параметров методов и членов класса.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Отладка основные понятия](../../extensibility/debugger/debugger-concepts.md)  
 Описывает основные архитектурные понятия отладки.  
  
 [Компоненты отладки](../../extensibility/debugger/debugger-components.md)  
 Обзор компонентов отладки Visual Studio, которые включают модуль отладки (DE), средство оценки выражений (EE) и символ обработчик (SH).  
  
 [Задачи отладки](../../extensibility/debugger/debugging-tasks.md)  
 Содержит ссылки на различные задачи отладки, такие как запуск программы и оценки выражений.
