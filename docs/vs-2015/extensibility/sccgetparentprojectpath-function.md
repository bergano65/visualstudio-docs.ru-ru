---
title: Функция SccGetParentProjectPath | Документация Майкрософт
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
- SccGetParentProjectPath
helpviewer_keywords:
- SccGetParentProjectPath function
ms.assetid: 62a71579-36b3-48b9-a1c8-04ab100efa08
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0e75c3e39f2d4f56d40ca546291b2f86bd185f88
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744411"
---
# <a name="sccgetparentprojectpath-function"></a>Функция SccGetParentProjectPath
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта функция определяет родительский путь проекта для указанного проекта. Эта функция вызывается, когда пользователь добавляет в проект Visual Studio для системы управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccGetParentProjectPath(  
   LPVOID pContext,  
   HWND   hWnd,  
   LPSTR  lpUser,  
   LPCSTR lpProjPath,  
   LPSTR  lpAuxProjPath,  
   LPSTR  lpParentProjPath  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.  
  
 lpUser  
 [in, out] Имя пользователя (до SCC_USER_SIZE, включая символ конца строки NULL).  
  
 lpProjPath  
 [in] Строка, определяющая путь к проекту (до SCC_PRJPATH_SIZE, включая символ конца строки NULL).  
  
 lpAuxProjPath  
 [in, out] Вспомогательный строка, определяющая проекта (до SCC_PRJPATH_SIZE, включая символ конца строки NULL).  
  
 lpParentProjPath  
 [in, out] Выходная строка идентификации родительский путь проекта (до SCC_PRJPATH_SIZE, включая символ конца строки NULL).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Родительский путь проекта был успешно получен.|  
|SCC_E_INITIALIZEFAILED|Не удалось инициализировать проект.|  
|SCC_E_INVALIDUSER|Пользователю не удалось войти в систему управления версиями подключаемого модуля.|  
|SCC_E_UNKNOWNPROJECT|Проект не известно подключаемый модуль системы управления версиями.|  
|SCC_E_INVALIDFILEPATH|Путь к файлу недопустим или непригодным для использования.|  
|SCC_E_NOTAUTHORIZED|Пользователю запрещено для этой операции.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, из-за проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_PROJSYNTAXERR|Синтаксис недопустимый проект.|  
|SCC_E_CONNECTIONFAILURE|Проблемы с подключением Store.|  
|SCC_E_NONSPECIFICERROR<br /><br /> SCC_E_UNKNOWNERROR|Обнаружена неспецифическая ошибка.|  
  
## <a name="remarks"></a>Примечания  
 Эта функция возвращает код об успехе или неудаче и в случае успешного выполнения заполняет переменную `lpParentProjPath` с путем весь проект в указанный проект.  
  
 Эта функция возвращает родительский путь к проекту существующего проекта. Для корневой проект, функция возвращает путь к проекту, который был передан в (то есть же корневой путь проекта). Обратите внимание на то, что путь к проекту представляет собой строку, которая имеет смысл только для подключаемого модуля системы управления версиями.  
  
 Интегрированная среда разработки подготовлена для сохранения изменений в `lpUser` и `lpAuxProjPath` также параметры. Интегрированная среда разработки будет сохранять эти строки и передать их в [SccOpenProject](../extensibility/sccopenproject-function.md) при открытии этого проекта в будущем. Эти строки таким образом, представляют собой способ для системы управления версиями, подключаемый модуль для данных отслеживания, которые требуется связать с проектом.  
  
 Эта функция аналогична [SccGetProjPath](../extensibility/sccgetprojpath-function.md), за исключением того, что не предлагает пользователю выбрать проект. Он также не создает новый проект, но работает только с существующим проектом.  
  
 Когда `SccGetParentProjectPath` вызове `lpProjPath` и `lpAuxProjPath` не будет пустым и будет соответствовать допустимый проект. Эти строки, обычно принимаются IDE из предыдущего вызова `SccGetProjPath` функции.  
  
 `lpUser` Аргумент — это имя пользователя. Пользователь с одинаковым именем, он ранее получен от передаст интегрированной среды разработки `SccGetProjPath` функции и подключаемый модуль системы управления версиями следует использовать имя по умолчанию. Если пользователь уже имеет открытое соединение с помощью подключаемого модуля, подключаемый модуль должен попытаться устранить все запросы, чтобы убедиться в том, что функция работает автоматически. Тем не менее, если произойдет ошибка входа, подключаемый модуль должен запросить пользователя для имени входа, и, при получении является допустимым именем входа, передайте имя обратно в `lpUser`. Поскольку подключаемый модуль может изменить эту строку, IDE всегда будет выделять буфер размером (`SCC_USER_LEN`+ 1). Если строка изменяется, новый строка должна быть допустимым именем для входа (по крайней мере, как действует как старой строки).  
  
## <a name="technical-notes-for-scccreatesubproject-and-sccgetparentprojectpath"></a>Технические примечания с SccCreateSubProject и SccGetParentProjectPath  
 Добавление решений и проектов в систему управления версиями упрощен в Visual Studio, чтобы свести к минимуму количество раз, когда пользователю предлагается выбрать расположения в системе управления версиями. Эти изменения обычно активируются по Visual Studio, если подключаемый модуль системы управления версиями поддерживает обе новые функции, [SccCreateSubProject](../extensibility/scccreatesubproject-function.md) и `SccGetParentProjectPath` функции. Тем не менее чтобы отключить эти изменения и вернуться к предыдущему поведению Visual Studio (исходный элемент управления Plug-in API версии 1.1) можно использовать следующий параметр реестра:  
  
 [HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0\SourceControl] «DoNotCreateSolutionRootFolderInSourceControl» = DWORD: 00000001  
  
 Если этот параметр реестра не существует или имеет значение DWORD: 00000000, Visual Studio пытается использовать новые функции, `SccCreateSubProject`и`SccGetParentProjectPath`.  
  
 Если параметр имеет значение DWORD: 00000001, Visual Studio не будет пытаться использовать эти новые функции и операции добавления в систему управления версиями, работают как в предыдущих версиях Visual Studio.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [SccCreateSubProject](../extensibility/scccreatesubproject-function.md)   
 [SccGetProjPath](../extensibility/sccgetprojpath-function.md)

