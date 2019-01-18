---
title: Интерфейс IDispError | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b717ebfe740a9b356513bb0f15e90c629a14e147
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345842"
---
# <a name="idisperror-interface"></a>Интерфейс IDispError
Предоставляет подробные контекстные сведения об ошибке.  
  
> [!NOTE]
>  Этот интерфейс не реализован.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDispError` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDispError::QueryErrorInfo](../../winscript/reference/idisperror-queryerrorinfo.md)|Извлекает определенный тип сведений об ошибке.|  
|[IDispError::GetNext](../../winscript/reference/idisperror-getnext.md)|Извлекает следующий `IDispError` объекта.|  
|[IDispError::GetHresult](../../winscript/reference/idisperror-gethresult.md)|Получает код ошибки из `IDispError` объекта.|  
|[IDispError::GetSource](../../winscript/reference/idisperror-getsource.md)|Возвращает программный идентификатор зависит от языка для класса или приложения, в котором возникла ошибка.|  
|[IDispError::GetHelpInfo](../../winscript/reference/idisperror-gethelpinfo.md)|Возвращает путь к файлу справки и идентификатор раздела справки, который описывает ее, если это возможно.|  
|[IDispError::GetDescription](../../winscript/reference/idisperror-getdescription.md)|Возвращает текстовое описание ошибки.|