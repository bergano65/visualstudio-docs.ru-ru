---
title: Функция SccRemove (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccRemove
helpviewer_keywords:
- SccRemove function
ms.assetid: 20830fdc-c0e9-4a5f-bf60-33f28874442f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 17889d50dbdcf68dd4cca161d6703b8b6d69ad47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700456"
---
# <a name="sccremove-function"></a>Функция SccRemove
Эта функция удаляет файлы из системы управления исходным источником.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccRemove(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Параметры
 pvКонтекст

(в) Структура контекста управления исходным элементом.

 Hwnd

(в) Ручка к окну IDE, которую плагин управления исходным элементом может использоваться в качестве родительского элемента для любых диалоговых коробок, которые она предоставляет.

 nФайлы

(в) Количество файлов, указанных в массиве. `lpFileNames`

 lpFileNames

(в) Массив полностью квалифицированных локальных имен путей файлов, которые будут удалены.

 lpКомментарий

(в) Комментарий, который будет применяться к каждому файлу удаляется.

 fВарианты

(в) Флаги командования (неиспользованные).

 pvOptions

(в) Опции управления исходным управлением.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Удаление было успешным.|
|SCC_E_FILENOTCONTROLLED|Выбранный файл не находится под контролем источника.|
|SCC_E_OPNOTSUPPORTED|Система управления исходным источником не поддерживает эту операцию.|
|SCC_E_ISCHECKEDOUT|Не удается удалить файл, потому что пользователь в настоящее время он проверил.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления исходным кодом, вероятно, из-за проблем с сетью или раздором.|
|SCC_E_NOTAUTHORIZED|Пользователю не разрешается выполнять эту операцию.|
|SCC_E_NONSPECIFICERROR|Неспецифический сбой; файл не был удален.|
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|

## <a name="remarks"></a>Примечания
 Эта функция удаляет файлы из системы управления исходным источником, но не удаляет их с локального жесткого диска пользователя.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
