---
title: Функция SccGetParentProjectPath (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f258558207f86ff76746d18aa432fe4c5850290
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700718"
---
# <a name="sccgetparentprojectpath-function"></a>Функция SccGetParentProjectPath
Эта функция определяет траекторию родительского проекта указанного проекта. Эта функция вызывается, когда пользователь добавляет проект Visual Studio в элемент управления исходным элементом.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccGetParentProjectPath(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpProjPath,
   LPSTR  lpAuxProjPath,
   LPSTR  lpParentProjPath
);
```

### <a name="parameters"></a>Параметры
 pContext

(в) Указатель контекста управления исходным элементом.

 Hwnd

(в) Ручка к окну IDE, которую плагин управления исходным элементом может использоваться в качестве родительского элемента для любых диалоговых коробок, которые она предоставляет.

 lpUser

(в, вне) Имя пользователя (до SCC_USER_SIZE, включая терминатор NULL).

 lpProjPath

(в) Строка, определяющая траекторию проекта (до SCC_PRJPATH_SIZE, включая терминатор NULL).

 lpAuxProjPath

(в, вне) Вспомогательная строка, определяющая проект (до SCC_PRJPATH_SIZE, включая терминатор NULL).

 lpParentProjPath

(в, вне) Строка вывода, идентифицирующая траекторию родительского проекта (до SCC_PRJPATH_SIZE, включая терминатор NULL).

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Путь родительского проекта был успешно получен.|
|SCC_E_INITIALIZEFAILED|Проект не может быть инициализирован.|
|SCC_E_INVALIDUSER|Пользователь не смог войти в плагин управления исходным элементом.|
|SCC_E_UNKNOWNPROJECT|Проект неизвестен плагину управления исходным элементом.|
|SCC_E_INVALIDFILEPATH|Недействительный или непригодный для вхлых путей файла.|
|SCC_E_NOTAUTHORIZED|Пользователю не разрешается выполнять эту операцию.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления исходным кодом, вероятно, из-за проблем с сетью или раздором. Рекомендуется повторная попытка.|
|SCC_E_PROJSYNTAXERR|Недействительный синтаксис проекта.|
|SCC_E_CONNECTIONFAILURE|Проблема подключения магазина.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Неспецифический сбой.|

## <a name="remarks"></a>Примечания
 Эта функция возвращает код успеха или отказа и, `lpParentProjPath` в случае успеха, заполняет переменную полным маршрутом проекта к указанному проекту.

 Эта функция возвращает родительский путь проекта существующего проекта. Для корневого проекта функция возвращает пройдение пути проекта (т.е. тот же путь корневого проекта). Обратите внимание, что путь проекта — это строка, которая имеет значение только для плагина управления исходным управлением.

 IDE готов принять изменения и `lpUser` `lpAuxProjPath` в параметры. IDE будет сохранять эти строки и передавать их [в SccOpenProject,](../extensibility/sccopenproject-function.md) когда пользователь открывает этот проект в будущем. Таким образом, эти строки предоставляют возможность плагину управления исходным источником для отслеживания информации, необходимой для ассоциированной с проектом.

 Эта функция аналогична [SccGetProjPath](../extensibility/sccgetprojpath-function.md), за исключением того, что она не побуждает пользователя выбрать проект. Он также никогда не создает новый проект, но работает только с существующим проектом.

 Когда `SccGetParentProjectPath` `lpProjPath` называется, `lpAuxProjPath` и не будет пустым и будет соответствовать действительный проект. Эти строки обычно принимаются IDE от предыдущего вызова к функции. `SccGetProjPath`

 Аргументом `lpUser` является имя пользователя. IDE будет передаваться в том же имени пользователя, что он ранее получил от `SccGetProjPath` функции, и плагин управления исходным элементом должен использовать имя по умолчанию. Если пользователь уже имеет открытое соединение с плагином, то плагин должен попытаться устранить любые запросы, чтобы убедиться, что функция работает бесшумно. Однако, если логин не удается, плагин должен побудить пользователя для входа и, когда он `lpUser`получает действительный логин, передать имя обратно дюйма Поскольку плагин может изменить эту строку, IDE всегда`SCC_USER_LEN`будет выделять буфер размера (No1). Если строка изменена, новая строка должна быть действительным именем входа (по крайней мере, так же действительны, как старая строка).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Технические заметки для SccCreateSubProject и SccGetParentProjectPath
 Добавление решений и проектов к управлению исходными данными было упрощено в Visual Studio, чтобы свести к минимуму количество раз, когда пользователю предлагается выбрать местоположения в системе управления исходным источником. Эти изменения активируются Visual Studio, если плагин управления исходным источником поддерживает обе новые функции, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) и функцию. `SccGetParentProjectPath` Тем не менее, следующая запись реестра может быть использована для отключения этих изменений и возврата к предыдущему поведению Visual Studio (Source Control Plug-in API Version 1.1):

 **«HKEY_CURRENT_USER»Программное обеспечение»Microsoft,VisualStudio»8.0 (SourceControl) "DoNotCreateSolutionRootFolderInSourceControl"**

 Если эта запись реестра не существует или установлена на dword:000000000, Visual `SccCreateSubProject``SccGetParentProjectPath`Studio пытается использовать новые функции, и .

 Если запись в реестре установлена на dword:000000001, Visual Studio не пытается использовать эти новые функции, а операции по добавлению к работе управления исходным источником, как это было в предыдущих версиях Visual Studio.

## <a name="see-also"></a>См. также
- [Функции API управления исходным элементом](../extensibility/source-control-plug-in-api-functions.md)
- [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
