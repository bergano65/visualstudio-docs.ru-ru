---
title: "Функция SccCreateSubProject | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccCreateSubProject
helpviewer_keywords: SccCreateSubProject function
ms.assetid: 08154aed-ae5c-463c-8694-745d0e332965
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 97993833d08479fbf518fb5b4852f46cc34f9bc3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="scccreatesubproject-function"></a>Функция SccCreateSubProject
Эта функция создает подпроект с заданным именем в существующий проект родительского заданные `lpParentProjPath` аргумент.  
  
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
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для все диалоговые окна, которые он предоставляет.  
  
 lpUser  
 [in, out] Имя пользователя (до SCC_USER_SIZE, включая символ конца строки).  
  
 lpParentProjPath  
 [in] Строка, идентифицирующая путь родительского проекта (до SCC_PRJPATH_SIZE, включая символ конца строки).  
  
 lpSubProjName  
 [in] Имя предлагаемые подпроекта (до SCC_PRJPATH_SIZE, включая символ конца строки).  
  
 lpAuxProjPath  
 [in, out] Вспомогательный строка, определяющая проекта (до SCC_PRJPATH_SIZE, включая символ конца строки).  
  
 lpSubProjPath  
 [in, out] Выходная строка идентификации пути для подпроекта (до SCC_PRJPATH_SIZE, включая символ конца строки).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Подпроект успешно создан.|  
|SCC_E_INITIALIZEFAILED|Не удалось инициализировать родительский проект.|  
|SCC_E_INVALIDUSER|Пользователь не может войти систему управления версиями.|  
|SCC_E_COULDNOTCREATEPROJECT|Не удается создать подпроект.|  
|SCC_E_PROJSYNTAXERR|Проект недопустимый синтаксис.|  
|SCC_E_UNKNOWNPROJECT|Родительский проект неизвестен подключаемый модуль системы управления версиями.|  
|SCC_E_INVALIDFILEPATH|Путь к файлу недопустим или недоступным для использования.|  
|SCC_E_NOTAUTHORIZED|Для выполнения этой операции не разрешено пользователю.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_CONNECTIONFAILURE|Возникла проблема подключения подключаемого модуля управления источника.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Неспецифичную сбоя.|  
  
## <a name="remarks"></a>Примечания  
 Если подпроект с именем уже существует, функция может изменить имя по умолчанию для создания уникальных, например путем добавления «_\<номер >» к нему. Вызывающий объект должен быть готов к внесению изменений `lpUser`, `lpSubProjPath`, и `lpAuxProjPath`. `lpSubProjPath` И`lpAuxProjPath` аргументы будут использоваться в вызове [SccOpenProject](../extensibility/sccopenproject-function.md). Они не должны изменяться после возврата вызывающему объекту. Эти строки представляют собой способ для системы управления версиями для отслеживания сведений, которые требуется связать с проектом. Вызывающий объект интегрированной среды разработки не будут отображаться эти два параметра, после возврата, поскольку подключаемый модуль можно использовать строку форматирования, которая может оказаться неподходящим для просмотра. Функция возвращает успешное выполнение или сбой кода и в случае успешного выполнения заполняет переменную `lpSubProjPath` путем полного проекта в новый проект.  
  
 Эта функция аналогична [SccGetProjPath](../extensibility/sccgetprojpath-function.md), за исключением того, что автоматически создает проект, а не предлагая пользователю выбрать один. Когда `SccCreateSubProject` вызывается функция, `lpParentProjName` и `lpAuxProjPath` не может быть пустой и будет соответствовать допустимый проект. Эти строки, обычно полученных IDE из предыдущего вызова `SccGetProjPath` функции или [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md).  
  
 `lpUser` Аргумент — имя пользователя. Передает интегрированной среды разработки в том же имени пользователя, он ранее получен от `SccGetProjPath`, и подключаемый модуль системы управления версиями следует использовать имя по умолчанию. Если у пользователя уже есть открытое соединение с помощью подключаемого модуля, подключаемый модуль должен повторите во избежание каких-либо запросов, чтобы убедиться в том, что функция будет работать без вмешательства пользователя. Тем не менее, если вход не выполняется, подключаемый модуль должен запросить пользователя для имени входа, и, при получении действительного имени входа, передайте имя обратно в `lpUser`. Так как подключаемый модуль может изменить эту строку, интегрированной среды разработки будет всегда выделяется буфер размером (SCC_USER_LEN + 1 или SCC_USER_SIZE, который включает место для завершающего нуль-символа). Если строка изменяется, новую строку необходимо допустимое имя входа (по крайней мере допустимым значением старые строки).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Технические примечания для SccCreateSubProject и SccGetParentProjectPath  
 Добавление решений и проектов в систему управления версиями, был упрощен в Visual Studio, чтобы свести к минимуму количество раз, когда пользователю предлагается выбрать расположения в системе управления версиями. Эти изменения активируются по Visual Studio, если подключаемый модуль системы управления версиями поддерживает несколько новых функций, `SccCreateSubProject` и `SccGetParentProjectPath`. Тем не менее отключить эти изменения и вернуться к предыдущему поведению Visual Studio (источник управления Plug-in API версии 1.1) можно использовать следующий параметр реестра:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] «DoNotCreateSolutionRootFolderInSourceControl» = DWORD: 00000001  
  
 Если этот параметр реестра не существует или имеет значение DWORD: 00000000, пытается использовать новые функции Visual Studio `SccCreateSubProject` и `SccGetParentProjectPath`.  
  
 Если параметр имеет значение DWORD: 00000001, Visual Studio не будет пытаться использовать эти новые функции и операции добавления в систему управления версиями работать, как и в предыдущих версиях Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)