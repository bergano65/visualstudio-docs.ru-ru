---
title: "Документирование контекста | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5a38d0ad28ad01b9e106cf06127b934dedfe5bba
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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