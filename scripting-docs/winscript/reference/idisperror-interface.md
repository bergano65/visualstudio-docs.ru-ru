---
title: "Интерфейс IDispError | Документы Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9f139d317db5aa00f03f8e9abd71020e5ff35b03
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="idisperror-interface"></a>Интерфейс IDispError
Предоставляет подробные контекстные сведения об ошибке.  
  
> [!NOTE]
>  Этот интерфейс не реализован.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDispError` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Возвращает определенный тип сведений об ошибках.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Извлекает следующий `IDispError` объекта.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Получает код ошибки из `IDispError` объекта.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Возвращает программный идентификатор зависит от языка для класса или приложения, в котором возникла ошибка.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Возвращает путь к файлу справки и идентификатор контекста раздела справки, который описывает ее, если это возможно.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Возвращает текстовое описание ошибки.|