---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 296502aa461688c34152d86ee21aab5f2c83ecb4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62956748"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Вызывается непосредственно перед выгрузкой управляемой надстройки VSTO.

## <a name="syntax"></a>Синтаксис

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Возвращаемое значение
 Значение HRESULT, указывающее, успешно ли завершен метод.

## <a name="remarks"></a>Примечания
 Этот метод не вызывается текущими версиями Microsoft Office. Этот метод зарезервирован для использования в будущем.

## <a name="see-also"></a>См. также
- [Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
