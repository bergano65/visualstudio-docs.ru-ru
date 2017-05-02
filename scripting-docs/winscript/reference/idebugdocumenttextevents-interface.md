---
title: "Интерфейс IDebugDocumentTextEvents | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentTextEvents — интерфейс"
ms.assetid: 341b20fd-994c-4030-a06b-6c66ad38c35d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugDocumentTextEvents
Предоставляет события, указывающий изменения в связанный обработчик действия текстовый документ.  
  
> [!NOTE]
>  Рисование текста изменяется, когда события в этом взаимодействуют пожар.  Обработчики событий могут получить новый текст с помощью интерфейса `IDebugDocumentText`.  
  
 В дополнение к методам, наследуемым от интерфейса `IUnknown`, интерфейс `IDebugDocumentTextEvents` предоставляет следующие методы.  
  
## Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugDocumentTextEvents::onDestroy](../../winscript/reference/idebugdocumenttextevents-ondestroy.md)|Указывает, что базовый документ был удален и более не допустимы|  
|[IDebugDocumentTextEvents::onInsertText](../../winscript/reference/idebugdocumenttextevents-oninserttext.md)|Указывает, что было добавитьо нового текста в документ|  
|[IDebugDocumentTextEvents::onRemoveText](../../winscript/reference/idebugdocumenttextevents-onremovetext.md)|Указывает, что текст был удалитьо из документа.|  
|[IDebugDocumentTextEvents::onReplaceText](../../winscript/reference/idebugdocumenttextevents-onreplacetext.md)|Указывает, что текст был заменитьо.|  
|[IDebugDocumentTextEvents::onUpdateTextAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatetextattributes.md)|Указывает, что атрибуты текста, связанные с основным диапазоном позиции символа.|  
|[IDebugDocumentTextEvents::onUpdateDocumentAttributes](../../winscript/reference/idebugdocumenttextevents-onupdatedocumentattributes.md)|Указывает, что атрибуты документа.|