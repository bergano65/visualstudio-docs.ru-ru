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
ms.openlocfilehash: e39693f63ea706ecdfa30a9ce0202444f51d4f57
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56616109"
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

## <a name="see-also"></a>См. также раздел
- [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)