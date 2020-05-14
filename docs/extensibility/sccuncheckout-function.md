---
title: Функция SccUncheckout (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUncheckout
helpviewer_keywords:
- SccUncheckout function
ms.assetid: 6d498b70-29c7-44b7-ae1c-7e99e488bb09
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4317133b2f215e0f9af447e5c042785561231f63
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700250"
---
# <a name="sccuncheckout-function"></a>Функция SccUncheckout
Эта функция отменяет предыдущую операцию проверки, тем самым восстанавливая содержимое выбранного файла или файлов в состояние до оформления заказа. Все изменения, внесенные в файл после проверки, потеряны.

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
 pvКонтекст

(в) Структура контекста управления исходным элементом.

 Hwnd

(в) Ручка к окну IDE, которую плагин управления исходным элементом может использоваться в качестве родительского элемента для любых диалоговых коробок, которые она предоставляет.

 nФайлы

(в) Количество файлов, указанных в массиве. `lpFileNames`

 lpFileNames

(в) Массив полностью квалифицированных локальных имен путей файлов, для которых можно отменить оформление.

 fВарианты

(в) Флаги командования (не используются).

 pvOptions

(в) Опции управления исходным управлением.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Отменить выезд был успешным.|
|SCC_E_FILENOTCONTROLLED|Выбранный файл не находится под контролем исходного кода.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления исходным кодом, вероятно, из-за проблем с сетью или раздором. Рекомендуется повторная попытка.|
|SCC_E_NONSPECIFICERROR|Неспецифический сбой. Отменить выезд не удалось.|
|SCC_E_NOTCHECKEDOUT|Пользователь не имеет файл атедля.|
|SCC_E_NOTAUTHORIZED|Пользователю не разрешается выполнять эту операцию.|
|SCC_E_PROJNOTOPEN|Проект не был открыт из-за элемента управления исходом.|
|SCC_I_OPERATIONCANCELED|Операция была отменена до завершения.|

## <a name="remarks"></a>Примечания
 После этой `SCC_STATUS_CHECKEDOUT` операции, `SCC_STATUS_MODIFIED` и флаги будут очищены для файлов, на которых была выполнена отменить выезд.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
