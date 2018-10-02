---
title: POPDIRLISTFUNC | Документация Майкрософт
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
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ed4cb154b1b1f74a6b0b6e64063a826b80364dd3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568924"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [POPDIRLISTFUNC](https://docs.microsoft.com/visualstudio/extensibility/popdirlistfunc).  
  
Это функция обратного вызова, присвоенный [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) функции, чтобы обновить коллекцию каталогов и (необязательно) имена файлов, чтобы узнать, которые являются в системе управления версиями.  
  
 `POPDIRLISTFUNC` Обратного вызова должен вызываться только для этих имен файлов и папок (в списке, присвоенный `SccPopulateDirList` функции), которые фактически в системе управления версиями.  
  
## <a name="signature"></a>Подпись  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Параметры  
 pvCallerData  
 [in] Значение пользователя, присвоенный [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md).  
  
 bFolder  
 [in] `TRUE` Если имя в `lpDirectoryOrFileName` является каталогом; в противном случае имя является именем файла.  
  
 lpDirectoryOrFileName  
 [in] Полный локальный путь к имени файла или каталога, в системе управления версиями.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Интегрированная среда разработки возвращает код соответствующее сообщение об ошибке:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Продолжайте обработку.|  
|SCC_I_OPERATIONCANCELED|Остановите обработку.|  
|SCC_E_xxx|Любая ошибка соответствующего исходного элемента управления следует остановить обработку.|  
  
## <a name="remarks"></a>Примечания  
 Если `fOptions` параметр `SccPopulateDirList` функция содержит `SCC_PDL_INCLUDEFILES` флаг, то список будет содержать имена файлов, а также имена каталогов.  
  
## <a name="see-also"></a>См. также  
 [Функции обратного вызова, реализованные интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)   
 [Коды ошибок](../extensibility/error-codes.md)

