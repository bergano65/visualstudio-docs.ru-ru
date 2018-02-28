---
title: "POPDIRLISTFUNC | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 8503afb26ec8dc244db39dff5bddcc6d3b733896
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
Функция обратного вызова, присвоенное [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) функции, чтобы обновить коллекцию для каталогов и (необязательно) имена файлов, чтобы узнать, что в системе управления версиями.  
  
 `POPDIRLISTFUNC` Обратного вызова должен вызываться только для тех имен файлов и папок (в списке, присвоенное `SccPopulateDirList` функции), фактически являются в системе управления версиями.  
  
## <a name="signature"></a>Подпись  
  
```cpp  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Параметры  
 pvCallerData  
 [in] Пользовательское значение, присвоенное [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bFolder  
 [in] `TRUE` Если имя в `lpDirectoryOrFileName` является каталогом; в противном случае имя является именем файла.  
  
 lpDirectoryOrFileName  
 [in] Полный путь к локальному каталогу или файлу имя, в системе управления версиями.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Интегрированная среда разработки возвращается код соответствующее сообщение об ошибке:  
  
|Значение|Описание:|  
|-----------|-----------------|  
|SCC_OK|Продолжайте обработку.|  
|SCC_I_OPERATIONCANCELED|Останавливает обработку.|  
|SCC_E_xxx|Любая ошибка соответствующего исходного элемента управления должен остановить обработку.|  
  
## <a name="remarks"></a>Примечания  
 Если `fOptions` параметр `SccPopulateDirList` функция содержит `SCC_PDL_INCLUDEFILES` флагом список будет содержать имена файлов, а также имена каталогов.  
  
## <a name="see-also"></a>См. также  
 [Функции обратного вызова, реализуемый интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Коды ошибок](../extensibility/error-codes.md)