---
title: IDiaStackWalker::getEnumFrames | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalker2::getEnumFrames method
ms.assetid: f9f09729-4c34-441c-989c-e0b7339ee32c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9011f0becd893fa4ca966c40013844b0be47e46d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629395"
---
# <a name="idiastackwalkergetenumframes"></a>IDiaStackWalker::getEnumFrames
Извлекает перечислитель кадр стека для x86 платформ.

## <a name="syntax"></a>Синтаксис

```C++
HRESULT getEnumFrames( 
   IDiaStackWalkHelper*   pHelper,
   IDiaEnumStackFrames**  ppEnum
);
```

#### <a name="parameters"></a>Параметры
 `pHelper`

[in] Вспомогательный метод [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md) объекта.

 `ppEnum`

[out] Возвращает [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md) , содержащий список [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md) объектов.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Чтобы получить список кадров стека в любой другой платформы, вызовите [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md) метод.

## <a name="see-also"></a>См. также раздел
- [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)
- [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)
- [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)
- [IDiaStackWalker::getEnumFrames2](../../debugger/debug-interface-access/idiastackwalker-getenumframes2.md)