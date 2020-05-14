---
title: Функция SccCreateSubProject (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 74354e05b16830f599dd706fbe48aadd75b11a18
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701039"
---
# <a name="scccreatesubproject-function"></a>Функция SccCreateSubProject
Эта функция создает подпроект с указанным именем в `lpParentProjPath` рамках существующего родительского проекта, указанного аргументом.

## <a name="syntax"></a>Синтаксис

```cpp
SCCRTN SccCreateSubProject(
   LPVOID pContext,
   HWND   hWnd,
   LPSTR  lpUser,
   LPCSTR lpParentProjPath,
   LPCSTR lpSubProjName,
   LPSTR  lpAuxProjPath,
   LPSTR  lpSubProjPath
);
```

### <a name="parameters"></a>Параметры
 pContext

(в) Указатель контекста управления исходным элементом.

 Hwnd

(в) Ручка к окну IDE, которую плагин управления исходным элементом может использоваться в качестве родительского элемента для любых диалоговых коробок, которые она предоставляет.

 lpUser

(в, вне) Имя пользователя (до SCC_USER_SIZE, включая терминатор NULL).

 lpParentProjPath

(в) Строка, определяющая траекторию родительского проекта (до SCC_PRJPATH_SIZE, включая терминатор NULL).

 lpSubProjName

(в) Предлагаемое название подпроекта (до SCC_PRJPATH_SIZE, включая терминатор NULL).

 lpAuxProjPath

(в, вне) Вспомогательная строка, определяющая проект (до SCC_PRJPATH_SIZE, включая терминатор NULL).

 lpSubProjPath

(в, вне) Строка вывода, определяющая траекторию для подпроекта (до SCC_PRJPATH_SIZE, включая терминатор NULL).

## <a name="return-value"></a>Возвращаемое значение
 Ожидается, что внедрение этой функции элемента управления исходным элементом вернет одно из следующих значений:

|Значение|Описание|
|-----------|-----------------|
|SCC_OK|Успешно создан субпроект.|
|SCC_E_INITIALIZEFAILED|Родительский проект не может быть инициализирован.|
|SCC_E_INVALIDUSER|Пользователь не может войти в систему управления исходным источником.|
|SCC_E_COULDNOTCREATEPROJECT|Субпроект не может быть создан.|
|SCC_E_PROJSYNTAXERR|Недействительный синтаксис проекта.|
|SCC_E_UNKNOWNPROJECT|Родительский проект неизвестен плагину управления исходным элементом.|
|SCC_E_INVALIDFILEPATH|Недействительный или непригодный для вхлых путей файла.|
|SCC_E_NOTAUTHORIZED|Пользователю не разрешается выполнять эту операцию.|
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления исходным кодом, вероятно, из-за проблем с сетью или раздором. Рекомендуется повторная попытка.|
|SCC_E_CONNECTIONFAILURE|Возникла проблема с подключением к подключению к источнику управления.|
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Неспецифический сбой.|

## <a name="remarks"></a>Примечания
 Если подпроект с именем уже существует, функция может изменить имя по умолчанию,\<чтобы создать уникальное, например, добавив в него ">" " Звонящее должно быть готово `lpUser` `lpSubProjPath`принять `lpAuxProjPath`изменения к, и . `lpSubProjPath` Аргументы`lpAuxProjPath` и аргументы затем используются в вызове в [SccOpenProject](../extensibility/sccopenproject-function.md). Они не должны быть изменены абонентом по возвращении. Эти строки предоставляют возможность для плагина управления исходным источником для отслеживания информации, которую он должен связать с проектом. IDE вызывая не будет отображать эти два параметра по возвращении, потому что плагин может использовать отформатированную строку, которая может не подходить для просмотра. Функция возвращает код успеха или отказа и, в `lpSubProjPath` случае успеха, заполняет переменную полным путем проекта к новому проекту.

 Эта функция похожа на [SccGetProjPath](../extensibility/sccgetprojpath-function.md), за исключением того, что он молча создает проект, а не побуждение пользователя, чтобы выбрать один. Когда `SccCreateSubProject` функция `lpParentProjName` вызывается, `lpAuxProjPath` и не будет пустым и будет соответствовать допустимому проекту. Эти строки обычно получаются IDE от предыдущего вызова к `SccGetProjPath` функции или [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).

 Аргументом `lpUser` является имя пользователя. IDE будет передаваться в том же имени `SccGetProjPath`пользователя, что он ранее получил от , и плагин управления исходным элементом должен использовать имя по умолчанию. Если пользователь уже имеет открытое соединение с плагином, то плагин должен попытаться устранить любые запросы, чтобы убедиться, что функция работает бесшумно. Однако, если логин не удается, плагин должен побудить пользователя для входа и, когда он `lpUser`получает действительный логин, передать имя обратно дюйма Поскольку плагин может изменить эту строку, IDE всегда будет выделять буфер размера (SCC_USER_LEN no 1 или SCC_USER_SIZE, который включает в себя пространство для терминатора null). Если строка изменена, новая строка должна быть действительным именем входа (по крайней мере, так же действительны, как старая строка).

## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Технические заметки для SccCreateSubProject и SccGetParentProjectPath
 Добавление решений и проектов к управлению исходными данными было упрощено в Visual Studio, чтобы свести к минимуму количество раз, когда пользователю предлагается выбрать местоположения в системе управления исходным источником. Эти изменения активируются Visual Studio, если плагин управления исходным `SccCreateSubProject` `SccGetParentProjectPath`источником поддерживает обе новые функции, так и . Тем не менее, следующая запись реестра может быть использована для отключения этих изменений и возврата к предыдущему поведению Visual Studio (Source Control Plug-in API Version 1.1):

 **«HKEY_CURRENT_USER»Программное обеспечение»Microsoft,VisualStudio»8.0 (SourceControl) "DoNotCreateSolutionRootFolderInSourceControl"**

 Если эта запись реестра не существует или установлена на dword:000000000, Visual `SccCreateSubProject` `SccGetParentProjectPath`Studio пытается использовать новые функции, и .

 Если запись в реестре установлена на dword:000000001, Visual Studio не пытается использовать эти новые функции, а операции по добавлению к работе управления исходным источником, как это было в предыдущих версиях Visual Studio.

## <a name="see-also"></a>См. также
- [Функции API управления исходным элементом](../extensibility/source-control-plug-in-api-functions.md)
- [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)
- [SccGetProjPath](../extensibility/sccgetprojpath-function.md)
