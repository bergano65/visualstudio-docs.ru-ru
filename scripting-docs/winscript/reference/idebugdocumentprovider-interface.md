---
title: Интерфейс IDebugDocumentProvider | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: d775deb153205d0e9a452775272285c67e74a210
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345218"
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