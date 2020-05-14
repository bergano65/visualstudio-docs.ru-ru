---
title: Функция SccDir'ruryInfo Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccDirQueryInfo
helpviewer_keywords:
- SccDirQueryInfo function
ms.assetid: 459e2d99-573d-47c4-b834-6d82c5e14162
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 222b5d15a1e2bcd9bd3f27a5cd0e9904642d9786
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700952"
---
# <a name="sccdirqueryinfo-function"></a>Функция SccDir-''ведомостиИнфо
Эта функция рассматривает список полностью квалифицированных каталогов для их текущего состояния.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccDirQueryInfo(
LPVOID  pContext,
LONG    nDirs,
LPCSTR* lpDirNames,
LPLONG  lpStatus
);
```

### <a name="parameters"></a>Параметры
 pContext

(в) Структура контекста управления исходным элементом.

 nDirs

(в) Количество каталогов, выбранных для запроса.

 lpDirNames

(в) Массив полностью квалифицированных путей каталогов, которые будут запрошены.

 lpStatus

(в, вне) Структура массива для плагина управления исходным кодом для возврата флагов статуса (см. [код состояния каталога](../extensibility/directory-status-code-enumerator.md) для деталей).

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Запрос был успешным.|
|SCC_E_OPNOTSUPPORTED|Система управления исходным кодом не поддерживает эту операцию.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления исходным кодом, вероятно, из-за проблем с сетью или раздором. Рекомендуется повторная попытка.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Неспецифический сбой.|

## <a name="remarks"></a>Примечания
 Функция заполняет массив возврата битной машкой `SCC_DIRSTATUS` битов из семьи (см. [код состояния каталога),](../extensibility/directory-status-code-enumerator.md)одна запись для каждого приведенного каталога. Массив состояния выделяется абонентом.

 IDE использует эту функцию до того, как каталог будет переименован, чтобы проверить, находится ли каталог под контролем исходного кода, задав вопрос о том, есть ли у него соответствующий проект. Если каталог не находится под контролем источника, IDE может предоставить пользователю соответствующее предупреждение.

> [!NOTE]
> Если плагин управления исходным элементом не выполняет одно или несколько значений состояния, нереализованные биты должны быть сведены к нулю.

## <a name="see-also"></a>См. также
- [Функции API управления исходным элементом](../extensibility/source-control-plug-in-api-functions.md)
- [Код состояния каталога](../extensibility/directory-status-code-enumerator.md)
