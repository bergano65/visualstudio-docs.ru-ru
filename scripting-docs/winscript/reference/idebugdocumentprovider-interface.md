---
title: "Интерфейс IDebugDocumentProvider | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 262794718e238068cfd9a8e3fae5161b9fe8cc54
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idebugdocumentprovider-interface"></a>Интерфейс IDebugDocumentProvider
Предоставляет средства для создания документа по требованию.  
  
## <a name="remarks"></a>Примечания  
 Это означает косвенных для создания документа:  
  
-   Позволяет при необходимости загружать документ.  
  
-   Позволяет объекту документа должны находиться в пределах IDE отладчик.  
  
-   Обеспечивает несколько способов доступа к объект того же документа.  
  
 Это эффективно отделяет его от его поставщика и позволяет поставщику содержат дополнительные сведения о контексте времени выполнения.  
  
 Помимо методов, наследуемых от `IDebugDocumentInfo`, `IDebugDocumentProvider` интерфейс предоставляет следующие методы.  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|Документа, будет создан в том случае, если он еще не существует.|