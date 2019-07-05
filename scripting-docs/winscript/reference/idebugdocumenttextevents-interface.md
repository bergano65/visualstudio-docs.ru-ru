---
title: Интерфейс IDebugDocumentTextEvents | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentTextEvents interface
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7c83a6e3a41ed7087338989d5cb077fa070e724b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63434266"
---
# <a name="idebugdocumenttextevents-interface"></a>Интерфейс IDebugDocumentTextEvents
Предоставляет события, указывающие на изменения в сопоставленном текстовом документе.  
  
> [!NOTE]
> Текст документа изменяется, если события для данного интерфейса пожара. Обработчики событий могут получить новый текст с помощью `IDebugDocumentText` интерфейс.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugDocumentTextEvents` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Указывает, что базовый документ был удален и больше не является допустимым|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Указывает, что новый текст был добавлен в документ|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Указывает, что текст был удален из документа.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Указывает, что текст был заменен.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Указывает, что текст атрибуты, связанные с базовой позиция диапазона знаков были изменены.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Указывает, что изменить атрибуты документа.|