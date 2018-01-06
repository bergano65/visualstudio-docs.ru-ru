---
title: "Функция SccAddFilesFromSCC | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: SccAddFilesFromSCC
helpviewer_keywords: SccAddFilesFromSCC function
ms.assetid: f21a3500-ade8-4dd8-8647-10e2179be9c1
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 5bd53307323b1db4d5fa9e5407c3a0516f1187f4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
  
#### <a name="parameters"></a>Параметры  
 pContext  
 [in] Подключаемый модуль Контекстный указатель исходного элемента управления.  
  
 hWnd  
 [in] Дескриптор окна интегрированной среды разработки, подключаемый модуль системы управления версиями можно использовать в качестве родительского для все диалоговые окна, которые он предоставляет.  
  
 lpUser  
 [in, out] Имя пользователя (до SCC_USER_SIZE, включая завершающий символ null).  
  
 lpAuxProjPath  
 [in, out] Вспомогательный строка, определяющая проекта (до `SCC_PRJPATH_`размер, включая завершающий символ null).  
  
 cFiles  
 [in] Число файлов, предоставленных `lpFilePaths`.  
  
 lpFilePaths  
 [in, out] Массив имен файлов для добавления в текущий проект.  
  
 lpDestination  
 [in] Целевой путь, где находятся файлы, которые требуется записать.  
  
 lpComment  
 [in] Примечание, которое должно применяться к каждому из добавленных файлов.  
  
 pbResults  
 [in, out] Массив флагов, набор в случае успеха (от нуля или равен TRUE) или сбоя ("ноль" или "FALSE") для каждого файла (размер массива должен быть по крайней мере `cFiles` long).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_E_PROJNOTOPEN|Проект не открыт.|  
|SCC_E_OPNOTPERFORMED|Соединение не в том же проекте, в соответствии с`lpAuxProjPath.`|  
|SCC_E_NOTAUTHORIZED|Пользователь не авторизован для обновления базы данных.|  
|SCC_E_NONSPECIFICERROR|Произошла неизвестная ошибка.|  
|SCC_I_RELOADFILE|Файл или проект должен быть перезагружен.|  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля системы управления версиями](../extensibility/source-control-plug-in-api-functions.md)