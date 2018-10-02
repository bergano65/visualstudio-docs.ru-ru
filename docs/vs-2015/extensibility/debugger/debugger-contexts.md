---
title: Контексты отладчика | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 79808036-b680-4e4c-9c61-4ed43aa11323
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7f24360b29557ef767d1a9a5f91a6f116db9ec12
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571559"
---
# <a name="debugger-contexts"></a>Контексты отладчика
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [контексты отладчика](https://docs.microsoft.com/visualstudio/extensibility/debugger/debugger-contexts).  
  
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

