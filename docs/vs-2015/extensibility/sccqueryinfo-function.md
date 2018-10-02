---
title: Функция SccQueryInfo | Документация Майкрософт
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
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b134310ecadd569a35d10c0f064ff785ad01f90
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558253"
---
# <a name="sccqueryinfo-function"></a>Функция SccQueryInfo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [функция SccQueryInfo](https://docs.microsoft.com/visualstudio/extensibility/sccqueryinfo-function).  
  
Эта функция получает сведения о состоянии для набора выбранных файлов в системе управления версиями.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
SCCRTN SccQueryInfo(  
   LPVOID  pvContext,  
   LONG    nFiles,  
   LPCSTR* lpFileNames,  
   LPLONG  lpStatus  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pvContext  
 [in] Структура подключаемого модуля контекста исходного элемента управления.  
  
 nFiles  
 [in] Число файлов, указанных в `lpFileNames` массива и длину `lpStatus` массива.  
  
 lpFileNames  
 [in] Массив имен файлов к запросам.  
  
 lpStatus  
 [in, out] Массив, в котором подключаемый модуль системы управления версиями Возвращает флаги состояния для каждого файла. Дополнительные сведения см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Подключаемый модуль реализации элемента управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Запрос выполнен успешно.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, возможно, причиной проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_PROJNOTOPEN|Проект не открыт в системе управления версиями.|  
|SCC_E_NONSPECIFICERROR|Обнаружена неспецифическая ошибка.|  
  
## <a name="remarks"></a>Примечания  
 Если `lpFileName` является пустой строкой, в настоящее время отсутствуют сведения о состоянии для обновления. В противном случае — это полный путь имя файла, для которого были изменены сведения о состоянии.  
  
 Массиву возвращаемых значений могут быть битовой `SCC_STATUS_xxxx` bits. Дополнительные сведения см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md). Система управления версиями может не поддерживать все типы бит. Например если `SCC_STATUS_OUTOFDATE` не предоставляется, просто не бита.  
  
 При использовании этой функции для извлечения файлов, обратите внимание на следующие `MSSCCI` состояние требований:  
  
-   `SCC_STATUS_OUTBYUSER` задается, если текущий пользователь извлек файл.  
  
-   `SCC_STATUS_CHECKEDOUT` нельзя назначить Если `SCC_STATUS_OUTBYUSER` имеет значение.  
  
-   `SCC_STATUS_CHECKEDOUT` задается только если файл извлечен в указанный рабочий каталог.  
  
-   Если файл извлечен текущим пользователем в каталоге, отличном от рабочем каталоге, `SCC_STATUS_OUTBYUSER` устанавливается, но `SCC_STATUS_CHECKEDOUT` не является.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля управления источника](../extensibility/source-control-plug-in-api-functions.md)   
 [Код состояния файла](../extensibility/file-status-code-enumerator.md)

