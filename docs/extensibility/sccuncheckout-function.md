---
title: Функция SccUncheckout | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4d50b321f96b6759d95a6d923222e5e0a92b2ee3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66338472"
---
# <a name="sccuncheckout-function"></a>Функция SccUncheckout
Эта функция отменяет предыдущей операции извлечения, благодаря чему восстанавливается содержимое выбранного файла или файлов в состояние до извлечения. Все изменения, внесенные в файл с момента извлечения будут утеряны.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccUncheckout (
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

#### <a name="parameters"></a>Параметры
 pvContext

[in] Структура подключаемого модуля контекста исходного элемента управления.

 hWnd

[in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.

 nFiles

[in] Число файлов, указанных в `lpFileNames` массива.

 lpFileNames

[in] Массив имен файлов, для которого нужно отменить извлечение полный локальный путь.

 Возможности

[in] Команда флаги (не используется).

 pvOptions

[in] Параметры конкретного подключаемого модуля системы управления версиями.

## <a name="return-value"></a>Возвращаемое значение
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Операция отмены извлечения успешно.|
|SCC_E_FILENOTCONTROLLED|Выбранный файл не существует в системе управления версиями.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка. Отменить извлечение завершилась неудачно.|
|SCC_E_NOTCHECKEDOUT|Пользователь не имеет извлеченный файл.|
|SCC_E_NOTAUTHORIZED|Пользователю запрещено для этой операции.|
|SCC_E_PROJNOTOPEN|Проект не был открыт из системы управления версиями.|
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|

## <a name="remarks"></a>Примечания
 После выполнения этой операции `SCC_STATUS_CHECKEDOUT` и `SCC_STATUS_MODIFIED` флаги оба очищается файлы, на которых была выполнена операция отмены извлечения.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)