---
title: Документирование контекста | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f97df9bc3c0a40a44379ba37f1b36d79cffb74e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="document-context"></a>Контекст документа
В [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] отладка, **контексту документа**:  
  
-   Представляет позицию в исходном файле. Для языков, где исходный файл может отсутствовать к контексту документа определяет позицию в документе, обычно создается с помощью среды выполнения. Например обработчик скриптов может создать документ из скрипта. Дополнительные сведения см. в разделе [позицию в документе](../../extensibility/debugger/document-position.md).  
  
-   Описание позиции в исходном документе, соответствующий контекст кода. Обработчик символ сопоставляется контекста документации, с помощью информации, создаваемой компилятором или интерпретатором контекст кода.  
  
-   Реализуется [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Контекст кода](../../extensibility/debugger/code-context.md)   
 [Символ поставщика](../../extensibility/debugger/symbol-provider.md)   
 [Интерфейсы поставщика символов](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Контексты отладчика](../../extensibility/debugger/debugger-contexts.md)