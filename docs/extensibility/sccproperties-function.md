---
title: Функция SccProperties Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccProperties
helpviewer_keywords:
- SccProperties function
ms.assetid: 1bed38c9-73d2-4474-9717-f9dc26a89cbe
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bf2dd87efbb50346093144db6e069eea30138e37
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700509"
---
# <a name="sccproperties-function"></a>Функция SccProperties
Эта функция отображает свойства управления исходным источником для файла или проекта.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccProperties (
   LPVOID pvContext,
   HWND   hWnd,
   LPCSTR lpFileName
);
```

#### <a name="parameters"></a>Параметры
 pvКонтекст

(в) Структура контекста управления исходным элементом.

 Hwnd

(в) Ручка к окну IDE, которую плагин управления исходным элементом может использоваться в качестве родительского элемента для любых диалоговых коробок, которые она предоставляет.

 lpFileName

(в) Полностью квалифицированное название пути файла или проекта.

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Свойства были успешно отображены.|
|SCC_I_RELOADFILE|Система управления версиями изменила свойства файла, поэтому IDE должен перезагрузить этот файл.|
|SCC_E_PROJNOTOPEN|Указанный проект не был открыт в управлении исходным источником.|
|SCC_E_NOTAUTHORIZED|Пользователь не имеет права просматривать свойства этого файла или проекта.|
|SCC_E_FILENOTCONTROLLED|Указанный файл или проект не находится под контролем источника.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Произошла неизвестная или общая ошибка.|

## <a name="remarks"></a>Примечания
 Плагин управления исходным элементом отображает свойства в собственном диалоговом поле.

 Свойства определяются плагином управления исходным элементом и могут отличаться от плагина до плагина. Если плагин позволяет пользователю изменить свойства управления исходным источником `SCC_I_RELOAD` файла, он должен вернуться, чтобы сигнализировать IDE о необходимости перезагрузки этого файла или проекта.

## <a name="see-also"></a>См. также
- [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)
