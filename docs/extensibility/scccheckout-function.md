---
title: Функция SccCheckout | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCheckout
helpviewer_keywords:
- SccCheckout function
ms.assetid: 06e9ecd7-fc09-40c1-9dd1-2b56c622c80b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e5160a2600a8eb3250702dd0836d812b668a3d1b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333879"
---
# <a name="scccheckout-function"></a>Функция SccCheckout
При наличии списка имен полного имени файла, эта функция извлекает их на локальный диск. Комментарий применяется ко всем файлам, проверяемого товара. Аргумент примечания могут быть `null` строка.

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
 pvContext

[in] Структура подключаемого модуля контекста исходного элемента управления.

 hWnd

[in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.

 nFiles

[in] Число файлов, выбранных для извлечения.

 lpFileNames

[in] Массив имен файлов для извлечения полный локальный путь.

 lpComment

[in] Комментарий для применения к каждой из выбранных файлов, проверяемого товара.

 Возможности

[in] Команда флагов (см. в разделе [битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)).

 pvOptions

[in] Параметры конкретного подключаемого модуля системы управления версиями.

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Извлечение выполнено успешно.|
|SCC_E_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|
|SCC_E_NOTAUTHORIZED|Пользователю запрещено для этой операции.|
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка. Файл не был извлечен.|
|SCC_E_ALREADYCHECKEDOUT|У пользователя уже есть извлеченный файл.|
|SCC_E_FILEISLOCKED|Файл заблокирован, Запрет создания новых версий.|
|SCC_E_FILEOUTEXCLUSIVE|Другой пользователь выполнит монопольного извлечения на этот файл.|
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)
- [Битовые флаги, используемые конкретными командами](../extensibility/bitflags-used-by-specific-commands.md)