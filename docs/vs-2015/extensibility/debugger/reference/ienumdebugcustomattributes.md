---
title: Иенумдебугкустоматтрибутес | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a0e1b361e99ef1e32a7dd327e531a1049f4009a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158076"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Перечисляет пользовательские атрибуты.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Поставщик символов реализует этот интерфейс для поддержки настраиваемых атрибутов (через интерфейс [идебугкустоматтрибуте](../../../extensibility/debugger/reference/idebugcustomattribute.md) ).  
  
## <a name="notes-for-callers"></a>Примечания для вызывающих объектов  
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) возвращает этот интерфейс.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IEnumDebugCustomAttributes` .  
  
|Метод|Описание|  
|------------|-----------------|  
|[Вперед](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Извлекает указанное число настраиваемых атрибутов в последовательности перечисления.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Пропускает указанное число настраиваемых атрибутов в последовательности перечисления.|  
|[Сброс](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Сбрасывает последовательность перечислений в начало.|  
|[Клонировать](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Создает перечислитель, который содержит то же состояние перечисления, что и текущий перечислитель.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Возвращает число настраиваемых атрибутов в перечислителе.|  
  
## <a name="requirements"></a>Требования  
 Заголовок: sh. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Интерфейсы поставщика символов](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
