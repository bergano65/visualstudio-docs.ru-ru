---
title: Интерфейс IDispError | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDispError interface
ms.assetid: 3dc7b55e-94ba-4669-b20a-1e011f2d07cf
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2c67ff6e458f8350ef36a8a454e017b3ce6ea114
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144931"
---
# <a name="idisperror-interface"></a>Интерфейс IDispError
Предоставляет подробные контекстные сведения об ошибке.  
  
> [!NOTE]
>  Этот интерфейс не реализован.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDispError` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание:|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Извлекает определенный тип сведений об ошибке.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Извлекает следующий `IDispError` объекта.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Получает код ошибки из `IDispError` объекта.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Возвращает программный идентификатор зависит от языка для класса или приложения, в котором возникла ошибка.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Возвращает путь к файлу справки и идентификатор раздела справки, который описывает ее, если это возможно.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Возвращает текстовое описание ошибки.|