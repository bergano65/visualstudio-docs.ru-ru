---
title: Интерфейс IDebugFormatter | Документация Майкрософт
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugFormatter interface
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f35d1b811a017895ca40f3325bd0ac456070184f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62979231"
---
# <a name="idebugformatter-interface"></a>Интерфейс IDebugFormatter
Позволяет языку или интегрированной среде разработки настроить преобразование значениями VARIANT или типами VARTYPE и строками.  
  
 Помимо методов, наследуемых от `IUnknown`, `IDebugFormatter` интерфейс предоставляет следующие методы.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
  
|Метод|Описание|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Возвращает строку, представляющую заданного значения типа VARIANT.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Возвращает значение VARIANT, содержащая заданную строку.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Возвращает строку, представляющую данное значение VARTYPE.|