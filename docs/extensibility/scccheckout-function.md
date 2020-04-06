---
title: Функция SccCheckout (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ed809e33a80bf2903c88550e97b28b1e0178bcd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701109"
---
# <a name="scccheckout-function"></a>Функция SccCheckout
Учитывая список полностью квалифицированных имен файлов, эта функция проверяет их на локальном диске. Комментарий распространяется на все проверяемые файлы. Аргумент комментария может `null` быть строкой.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccCheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LPCSTR    lpComment,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>Параметры
 pvКонтекст

(в) Структура контекста управления исходным элементом.

 Hwnd

(в) Ручка к окну IDE, которую плагин управления исходным элементом может использоваться в качестве родительского элемента для любых диалоговых коробок, которые она предоставляет.

 nФайлы

(в) Количество файлов, выбранных для проверки.

 lpFileNames

(в) Массив полностью квалифицированных локальных имен путей файлов, которые должны быть проверены.

 lpКомментарий

(в) Комментарий, который будет применяться к каждому из отобранных файлов, проверяемых.

 fВарианты

(в) Флаги команд [(см. Bitflags, используемые определенными командами).](../extensibility/bitflags-used-by-specific-commands.md)

 pvOptions

(в) Опции управления исходным управлением.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Отъезд был успешным.|
|SCC_E_FILENOTCONTROLLED|Выбранный файл не находится под контролем исходного кода.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления исходным кодом, вероятно, из-за проблем с сетью или раздором. Рекомендуется повторная попытка.|
|SCC_E_NOTAUTHORIZED|Пользователю не разрешается выполнять эту операцию.|
|SCC_E_NONSPECIFICERROR|Неспецифический сбой. Файл не был проверен.|
|SCC_E_ALREADYCHECKEDOUT|Пользователь уже проверил файл.|
|SCC_E_FILEISLOCKED|Файл заблокирован, запрещая создание новых версий.|
|SCC_E_FILEOUTEXCLUSIVE|Другой пользователь сделал эксклюзивную проверку этого файла.|
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|

## <a name="see-also"></a>См. также
- [Функции API управления исходным элементом](../extensibility/source-control-plug-in-api-functions.md)
- [Битфлаги, используемые определенными командами](../extensibility/bitflags-used-by-specific-commands.md)
