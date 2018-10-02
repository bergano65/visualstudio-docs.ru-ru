---
title: Функция SccAddFilesFromSCC | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5fbfdbfd926c3cd54f31f4b6b42d8baeacaff06
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557532"
---
# <a name="sccaddfilesfromscc-function"></a>Функция SccAddFilesFromSCC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функция SccAddFilesFromSCC](https://docs.microsoft.com/visualstudio/extensibility/sccaddfilesfromscc-function).  
  
Эта функция добавляет список файлов из системы управления версиями в настоящее время открытый проект.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccAddFilesFromSCC(  
   LPVOID  pContext,  
   HWND    hWnd,  
   LPSTR   lpUser,  
   LPSTR   lpAuxProjPath,  
   LONG    cFiles,  
   LPCSTR* lpFilePaths,  
   LPCSTR  lpDestination,  
   LPCSTR  lpComment,  
   LPBOOL  pbResults  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для любой диалоговых окон, которые он предоставляет.  
  
 lpUser  
 [in, out] Имя пользователя (до SCC_USER_SIZE, включая завершающий символ null).  
  
 lpAuxProjPath  
 [in, out] Вспомогательный строка, определяющая проекта (до `SCC_PRJPATH_`размер, включая завершающий символ null).  
  
 cFiles  
 [in] Число файлов, предоставляемых `lpFilePaths`.  
  
 lpFilePaths  
 [in, out] Массив имен файлов, чтобы добавить в текущий проект.  
  
 lpDestination  
 [in] Целевой путь, в которой находятся файлы должны быть записаны.  
  
 lpComment  
 [in] Комментарий, который будет применяться к каждой из добавленных файлов.  
  
 pbResults  
 [in, out] Массив флагов, которые являются набора в случае успеха (ненулевое значение или TRUE) или ошибка ("ноль" или "FALSE") для каждого файла (размер массива должен быть по крайней мере `cFiles` long).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Проект не открыт.|  
|SCC_E_OPNOTPERFORMED|Соединение не тот же проект, в соответствии с `lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Пользователь не авторизован для обновления базы данных.|  
|SCC_E_NONSPECIFICERROR|Неизвестная ошибка.|  
|SCC_I_RELOADFILE|Файл или проект должен быть перезагружен.|  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)

