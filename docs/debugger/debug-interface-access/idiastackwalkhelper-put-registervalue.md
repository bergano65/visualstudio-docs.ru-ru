---
title: IDiaStackWalkHelper::put_registerValue | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkHelper2::put_registerValue method
ms.assetid: 8f02ce54-ef59-455f-8aa6-dc26761c7aff
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59d076781e0f67ad9a2f2af02e7dc937042b0e71
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56620399"
---
# <a name="idiastackwalkhelperputregistervalue"></a>IDiaStackWalkHelper::put_registerValue
Задает значение регистра.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT put_registerValue ( 
   DWORD     index,
   ULONGLONG NewVal
);
```

#### <a name="parameters"></a>Параметры
 `index`

[in] Значение из [перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md) перечисление, определяющее, зарегистрируйтесь для записи.

 `NewVal`

[in] Новое значение регистра.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Несмотря на размер значения реализация следует хранить, что регистр обычно содержит только. Например 8-битным регистром будет содержать только младшие 8-битов заданного значения.

## <a name="see-also"></a>См. также раздел
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [Перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)