---
title: "Функция SccQueryInfo | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 7bda59c3bf674354e38fa306abe1fbb673f40e19
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="sccqueryinfo-function"></a>Функция SccQueryInfo
Эта функция получает сведения о состоянии для набора выбранных файлов в системе управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Исходная структура подключаемого модуля контекста элемента управления.  
  
 nFiles  
 [in] Число файлов, указанных в `lpFileNames` массива и длина `lpStatus` массива.  
  
 lpFileNames  
 [in] Массив имен файлов, которые будут запрашиваться.  
  
 lpStatus  
 [in, out] Массив, в котором подключаемый модуль системы управления версиями Возвращает флаги состояния для каждого файла. Дополнительные сведения см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализация подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Запрос успешно выполнен.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, причиной проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_PROJNOTOPEN|Проект не открыт в системе управления версиями.|  
|SCC_E_NONSPECIFICERROR|Неспецифичную сбоя.|  
  
## <a name="remarks"></a>Примечания  
 Если `lpFileName` является пустой строкой, в настоящее время нет сведений о состоянии для обновления. В противном случае — это полный путь имя файла, для которого были изменены сведения о состоянии.  
  
 Возвращаемый массив может быть Битовая маска `SCC_STATUS_xxxx` bits. Дополнительные сведения см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md). Система управления версиями могут не поддерживать все типы бит. Например если `SCC_STATUS_OUTOFDATE` не будет предлагаться, просто не бита.  
  
 При использовании этой функции для извлечения файлов, обратите внимание на следующие `MSSCCI` состояние требований:  
  
-   `SCC_STATUS_OUTBYUSER`будет установлен, если файл извлечен текущим пользователем.  
  
-   `SCC_STATUS_CHECKEDOUT`Нельзя задавать, если `SCC_STATUS_OUTBYUSER` имеет значение.  
  
-   `SCC_STATUS_CHECKEDOUT`устанавливается только если файл извлечен в указанный рабочий каталог.  
  
-   Если файл извлечен текущим пользователем в папке, отличной от рабочий каталог `SCC_STATUS_OUTBYUSER` устанавливается, но `SCC_STATUS_CHECKEDOUT` не является.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Код состояния файла](../extensibility/file-status-code-enumerator.md)