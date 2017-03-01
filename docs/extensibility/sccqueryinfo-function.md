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
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: a178aada6303ed21f51a6be66ba02b2145dcd694
ms.lasthandoff: 02/22/2017

---
# <a name="sccqueryinfo-function"></a>Функция SccQueryInfo
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
 [in] Число файлов, указанных в `lpFileNames` массива и длина `lpStatus` массива.  
  
 lpFileNames  
 [in] Массив имен файлов должны запрашиваться.  
  
 lpStatus  
 [in, out] Массив, в который модуль управления версиями Возвращает флаги состояния для каждого файла. Дополнительные сведения см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Реализации подключаемого модуля управления источника этой функции должен возвращать одно из следующих значений:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Запрос выполнен успешно.|  
|SCC_E_ACCESSFAILURE|Возникла проблема с доступом к системе управления версиями, вызванная, вероятно, проблемы с сетью или конфликтов. Рекомендуется повторить операцию.|  
|SCC_E_PROJNOTOPEN|Проект не открыт в системе управления версиями.|  
|SCC_E_NONSPECIFICERROR|Служебные сбоя.|  
  
## <a name="remarks"></a>Примечания  
 Если `lpFileName` является пустой строкой, в настоящее время отсутствуют сведения о состоянии для обновления. В противном случае — это полный путь файла, для которого были изменены сведения о состоянии.  
  
 Возвращаемый массив может быть Битовая маска `SCC_STATUS_xxxx` bits. Дополнительные сведения см. в разделе [код состояния файла](../extensibility/file-status-code-enumerator.md). Системы управления версиями может не поддерживать все типы бит. Например если `SCC_STATUS_OUTOFDATE` не предоставляется, просто не бита.  
  
 При использовании этой функции для извлечения файлов, обратите внимание на следующие `MSSCCI` состояние требования:  
  
-   `SCC_STATUS_OUTBYUSER`задается, если текущий пользователь извлек файл.  
  
-   `SCC_STATUS_CHECKEDOUT`Невозможно задать, если `SCC_STATUS_OUTBYUSER` имеет значение.  
  
-   `SCC_STATUS_CHECKEDOUT`задается только если файл извлечен в указанный рабочий каталог.  
  
-   Если файл извлечен текущим пользователем в каталоге, отличном от рабочий каталог `SCC_STATUS_OUTBYUSER` устанавливается, но `SCC_STATUS_CHECKEDOUT` не является.  
  
## <a name="see-also"></a>См. также  
 [Функции API подключаемого модуля источника элемента управления](../extensibility/source-control-plug-in-api-functions.md)   
 [Код состояния файла](../extensibility/file-status-code-enumerator.md)
