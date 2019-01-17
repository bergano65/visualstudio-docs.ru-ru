---
title: Интерфейс IDebugDocumentContext | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentContext interface
ms.assetid: 665ee08a-5c6a-4ab1-ab93-de376acc9a74
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 998a219e8a58927ca62ec90e6b105586a64bbf2b
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349586"
---
# <a name="idebugdocumentcontext-interface"></a>Интерфейс IDebugDocumentContext
Предоставляет абстрактное представление части документа, отладка которого выполняется. Для текстовых документов это представление состоит из диапазона позицию символа.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugDocumentContext` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugDocumentContext::GetDocument](../../winscript/reference/idebugdocumentcontext-getdocument.md)|Возвращает документ, содержащий этот контекст.|  
|[IDebugDocumentContext::EnumCodeContexts](../../winscript/reference/idebugdocumentcontext-enumcodecontexts.md)|Перечисляет контексты кода, связанный с данным контекстом документа.|