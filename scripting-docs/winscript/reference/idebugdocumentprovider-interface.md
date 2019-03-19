---
title: Интерфейс IDebugDocumentProvider | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentProvider interface
ms.assetid: 36510acf-1ef9-479c-a430-d3f09502f82c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5632134c86b5aa0e3cb769a68d2d4cfd944ff35c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58157214"
---
# <a name="idebugdocumentprovider-interface"></a>Интерфейс IDebugDocumentProvider
Предоставляет средства для создания экземпляра документа по требованию.  
  
## <a name="remarks"></a>Примечания  
 Это косвенных означает, что для создания экземпляра документа:  
  
- Позволяет при необходимости загружать документ.  
  
- Позволяет объекту документа должны содержаться в отладчике интегрированной среды разработки.  
  
- Предоставляет несколько способов получить доступ к один и тот же объект документа.  
  
  Это эффективно отделяет его от его поставщика а дополнительные сведения о контексте выполнения, поставщик.  
  
  Помимо методов, наследуемых от `IDebugDocumentInfo`, `IDebugDocumentProvider` интерфейс предоставляет следующие методы.  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDebugDocumentProvider::GetDocument](../../winscript/reference/idebugdocumentprovider-getdocument.md)|В результате документ создаваться, если он еще не существует.|