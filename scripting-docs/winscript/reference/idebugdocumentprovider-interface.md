---
title: "Интерфейс IDebugDocumentProvider | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugDocumentProvider — интерфейс"
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Интерфейс IDebugDocumentProvider
Предоставляет середины для того, чтобы документ по запросу.  
  
## Заметки  
 Этот косвенные середины для создания экземпляра документа.  
  
-   Разрешает документ для загрузки при необходимости.  
  
-   Позволяет объекту документа, которое должно содержаться внутри интегрированной среды разработки отладчика.  
  
-   Позволяет использовать несколько способов получить доступ к одному и тому же объект документа.  
  
 Это фактически отделяет документ из своего поставщика и позволяет поставщику для внесения дополнительную среде выполнения сведения о контексте.  
  
 В дополнение к методам, наследуемым от интерфейса `IDebugDocumentInfo`, интерфейс `IDebugDocumentProvider` предоставляет следующие методы.  
  
|Метод|Описание|  
|-----------|--------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Приводит к тому, что документ быть создан, если он еще не существует.|