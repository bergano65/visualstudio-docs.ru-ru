---
title: IManagedAddin::Unload
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7a36599259a38d0b9b8eb814a457b3625d593b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934602"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Вызывается непосредственно перед выгрузкой управляемой надстройки VSTO.

## <a name="syntax"></a>Синтаксис

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Возвращаемое значение
 Значение HRESULT, указывающее, успешно ли завершен метод.

## <a name="remarks"></a>Remarks
 Этот метод не вызывается текущими версиями Microsoft Office. Этот метод зарезервирован для использования в будущем.

## <a name="see-also"></a>См. также раздел
- [Интерфейс IManagedAddin](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
