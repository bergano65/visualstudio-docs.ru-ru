---
title: Функция SccAddFilesFromSCC | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccAddFilesFromSCC
helpviewer_keywords:
- SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b827e1f7e26fb98e9d49de4e9fe2388e46ee07cb
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49831176"
---
# <a name="sccaddfilesfromscc-function"></a>Функция SccAddFilesFromSCC
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
  
### <a name="parameters"></a>Параметры  
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
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)