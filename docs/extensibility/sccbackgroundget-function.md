---
title: Функция SccBackgroundGet (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccBackgroundGet
helpviewer_keywords:
- SccBackgroundGet function
ms.assetid: 69817e52-b9ac-4f4d-820b-2cc9c384f0dc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1c07076b6e257bd5519d19f841797fbc652f0c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701232"
---
# <a name="sccbackgroundget-function"></a>Функция SccBackgroundGet
Эта функция извлекает из исходного управления каждый из указанных файлов без взаимодействия с пользователем.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccBackgroundGet(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LONG    dwFlags,
   LONG    dwBackgroundOperationID
);
```

### <a name="parameters"></a>Параметры
 pContext

(в) Указатель контекста управления исходным элементом.

 nФайлы

(в) Количество файлов, указанных в массиве. `lpFileNames`

 lpFileNames

(в, вне) Массив имен файлов, которые необходимо получить.

> [!NOTE]
> Имена должны быть полностью квалифицированными локальными именами файлов.

 dwFlags

(в) Флаги`SCC_GET_ALL`командования `SCC_GET_RECURSIVE`(, ).

 dwBackgroundOperationID

(в) Уникальное значение, связанное с этой операцией.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Operation completed successfully (Операция выполнена успешно).|
|SCC_E_BACKGROUNDGETINPROGRESS|Поиск фона уже выполняется (плагин управления исходным кодом должен вернуть это только в том случае, если он не поддерживает одновременные пакетные операции).|
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|

## <a name="remarks"></a>Примечания
 Эта функция всегда вызывается на поток, отличный от той, которая загрузила плагин управления исходным управлением. Ожидается, что эта функция не вернется до тех пор, пока она не будет выполнена; однако, его можно вызвать множественные времена с множественными списками архивов, все в то же самое время.

 Использование аргумента `dwFlags` такое же, как [SccGet](../extensibility/sccget-function.md).

## <a name="see-also"></a>См. также
- [Функции API управления исходным элементом](../extensibility/source-control-plug-in-api-functions.md)
- [SccGet](../extensibility/sccget-function.md)
