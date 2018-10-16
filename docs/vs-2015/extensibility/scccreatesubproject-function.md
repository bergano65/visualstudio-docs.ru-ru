---
title: Функция SccCreateSubProject | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccCreateSubProject
helpviewer_keywords:
- SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e62e1567559898b198866fe3e67e9b5b53096273
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49232093"
---
# <a name="scccreatesubproject-function"></a>Функция SccCreateSubProject
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция создает подпроект с заданным именем в существующий родительский проект определяемое `lpParentProjPath` аргумент.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.  
  
 lpUser  
 [in, out] Имя пользователя (до SCC_USER_SIZE, включая символ конца строки NULL).  
  
 lpParentProjPath  
 [in] Строка, определяющая путь родительского проекта (до SCC_PRJPATH_SIZE, включая символ конца строки NULL).  
  
 lpSubProjName  
 [in] Имя предлагаемые подпроекта (до SCC_PRJPATH_SIZE, включая символ конца строки NULL).  
  
 lpAuxProjPath  
 [in, out] Вспомогательный строка, определяющая проекта (до SCC_PRJPATH_SIZE, включая символ конца строки NULL).  
  
 lpSubProjPath  
 [in, out] Выходная строка идентификации пути для подпроекта (до SCC_PRJPATH_SIZE, включая символ конца строки NULL).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Подпроект успешно создан.|  
|SCC_E_INITIALIZEFAILED|Не удалось инициализировать родительского проекта.|  
|SCC_E_INVALIDUSER|Пользователю не удалось войти в систему управления версиями.|  
|SCC_E_COULDNOTCREATEPROJECT|Невозможно создать подпроект.|  
|SCC_E_PROJSYNTAXERR|Синтаксис недопустимый проект.|  
|SCC_E_UNKNOWNPROJECT|Родительский проект неизвестен подключаемый модуль системы управления версиями.|  
|SCC_E_INVALIDFILEPATH|Путь к файлу недопустим или непригодным для использования.|  
|SCC_E_NOTAUTHORIZED|Пользователю запрещено для этой операции.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_CONNECTIONFAILURE|Возникла проблема подключения подключаемого модуля управления источника.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Обнаружена неспецифическая ошибка.|  
  
## <a name="remarks"></a>Примечания  
 Если подпроект с именем уже существует, функция может изменить имя по умолчанию, чтобы создать уникальный пароль, например путем добавления «_\<номер >» к нему. Вызывающий объект должен быть готовы принять изменения `lpUser`, `lpSubProjPath`, и `lpAuxProjPath`. `lpSubProjPath` И`lpAuxProjPath` аргументы будут использоваться в вызове [SccOpenProject](../extensibility/sccopenproject-function.md). Они не может изменяться в вызывающем объекте при возврате. Эти строки представляют собой способ для системы управления версиями подключаемого модуля для отслеживания сведений, необходимо связать с проектом. Вызывающий объект интегрированной среды разработки не отображает эти два параметра, при возврате, поскольку подключаемый модуль можно использовать форматированную строку, могут не подойти для просмотра. Функция возвращает код об успехе или неудаче и в случае успешного выполнения заполняет переменную `lpSubProjPath` с путем полного проекта в новый проект.  
  
 Эта функция аналогична [SccGetProjPath](../extensibility/sccgetprojpath-function.md), за исключением того, что он автоматически создает проект, а не предлагая пользователю выбрать один. Когда `SccCreateSubProject` вызывается функция, `lpParentProjName` и `lpAuxProjPath` не будет пустым и будет соответствовать допустимый проект. Эти строки, обычно принимаются IDE из предыдущего вызова `SccGetProjPath` функции или [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 `lpUser` Аргумент — это имя пользователя. Пользователь с одинаковым именем, он ранее получен от передаст интегрированной среды разработки `SccGetProjPath`, и подключаемый модуль системы управления версиями следует использовать имя по умолчанию. Если пользователь уже имеет открытое соединение с помощью подключаемого модуля, подключаемый модуль должен попытаться устранить все запросы, чтобы убедиться в том, что функция работает автоматически. Тем не менее, если произойдет ошибка входа, подключаемый модуль должен запросить пользователя для имени входа, и, при получении является допустимым именем входа, передайте имя обратно в `lpUser`. Поскольку подключаемый модуль может изменить эту строку, интегрированная среда разработки будет всегда выделяется буфер размером (SCC_USER_LEN + 1 или SCC_USER_SIZE, который включает свободное место для завершающего). Если строка изменяется, новый строка должна быть допустимым именем для входа (по крайней мере, как действует как старой строки).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Технические примечания с SccCreateSubProject и SccGetParentProjectPath  
 Добавление решений и проектов в систему управления версиями упрощен в Visual Studio, чтобы свести к минимуму количество раз, когда пользователю предлагается выбрать расположения в системе управления версиями. Эти изменения обычно активируются по Visual Studio, если подключаемый модуль системы управления версиями поддерживает обе новые функции, `SccCreateSubProject` и `SccGetParentProjectPath`. Тем не менее чтобы отключить эти изменения и вернуться к предыдущему поведению Visual Studio (исходный элемент управления Plug-in API версии 1.1) можно использовать следующий параметр реестра:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] «DoNotCreateSolutionRootFolderInSourceControl» = DWORD: 00000001  
  
 Если этот параметр реестра не существует или имеет значение DWORD: 00000000, Visual Studio пытается использовать новые функции, `SccCreateSubProject` и `SccGetParentProjectPath`.  
  
 Если параметр имеет значение DWORD: 00000001, Visual Studio не будет пытаться использовать эти новые функции и операции добавления в систему управления версиями, работают как в предыдущих версиях Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)

