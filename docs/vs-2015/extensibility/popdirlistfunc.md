---
title: ПОПДИРЛИСТФУНК | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 77e4701d3d8ec54fd37d6483f55b10a28af65b15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194047"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это функция обратного вызова, предоставляемая функции [сккпопулатедирлист](../extensibility/sccpopulatedirlist-function.md) для обновления коллекции каталогов и (необязательно) имен файлов, которые следует найти в системе управления версиями.  
  
 `POPDIRLISTFUNC`Обратный вызов должен вызываться только для тех каталогов и имен файлов (в списке, заданном для `SccPopulateDirList` функции), которые фактически находятся в системе управления версиями.  
  
## <a name="signature"></a>Подпись  
  
```cpp#  
typedef BOOL (*POPDIRLISTFUNC)(  
   LPVOID pvCallerData,  
   BOOL bFolder,  
   LPCSTR lpDirectoryOrFileName  
);  
```  
  
## <a name="parameters"></a>Параметры  
 пвкаллердата  
 окне Значение пользователя, заданное в [сккпопулатедирлист](../extensibility/sccpopulatedirlist-function.md).  
  
 бфолдер  
 [входные] `TRUE` значение, если имя в `lpDirectoryOrFileName` папке является каталогом; в противном случае — имя файла.  
  
 лпдиректорйорфиленаме  
 окне Полный локальный путь к каталогу или имени файла в системе управления исходным кодом.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Интегрированная среда разработки возвращает соответствующий код ошибки:  
  
|Значение|Описание|  
|-----------|-----------------|  
|SCC_OK|Продолжайте обработку.|  
|SCC_I_OPERATIONCANCELED|Останавливает обработку.|  
|SCC_E_xxx|Любая соответствующая ошибка системы управления версиями должна прерывать обработку.|  
  
## <a name="remarks"></a>Remarks  
 Если `fOptions` параметр `SccPopulateDirList` функции содержит `SCC_PDL_INCLUDEFILES` флаг, то список может содержать имена файлов, а также имена каталогов.  
  
## <a name="see-also"></a>См. также:  
 [Функции обратного вызова, реализованные интегрированной средой разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [сккпопулатедирлист](../extensibility/sccpopulatedirlist-function.md)   
 [Код ошибки](../extensibility/error-codes.md)
