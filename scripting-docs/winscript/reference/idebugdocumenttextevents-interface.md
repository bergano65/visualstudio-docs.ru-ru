---
title: "Интерфейс IDebugDocumentTextEvents | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 078cd468b64d30c20f48a3392aa4509ed054fc3d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumenttextevents-interface"></a>Интерфейс IDebugDocumentTextEvents
Предоставляет события, указывающие на изменения в текстовом документе.  
  
> [!NOTE]
>  Текст документа изменяется, если события для этого интерфейса запускаются. Обработчики событий могут получить новый текст с помощью `IDebugDocumentText` интерфейса.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugDocumentTextEvents` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Указывает, что базовый документ был удален и больше не действительна|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Указывает, что новый текст добавлен в документ|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Указывает, что текст был удален из документа.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Указывает, что текст был заменен.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Указывает, что изменились текст атрибуты, связанные с базовой позиции диапазона знаков.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Указывает, что изменить атрибуты документа.|