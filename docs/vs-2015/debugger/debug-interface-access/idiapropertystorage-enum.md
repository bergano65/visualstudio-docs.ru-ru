---
title: IDiaPropertyStorage::Enum | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::Enum
ms.assetid: 00e462da-980a-40b3-a2d6-75a25ee809e5
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 48b289ed1e376f224ec513e7a118691d75fc9b69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538852"
---
# <a name="idiapropertystorageenum"></a>IDiaPropertyStorage::Enum
Получает перечислитель для свойств в этом наборе.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT Enum ( 
   IEnumSTATPROPSTG** ppenum
);
```

#### <a name="parameters"></a>Параметры
 `ppenum`

[out] Возвращает `IEnumSTATPROPSTG` объект (в пространстве имен Microsoft.VisualStudio.OLE.Interop), представляющий перечисление свойств.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)