---
title: "OPTNAMECHANGEPFN | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OPTNAMECHANGEPFN
helpviewer_keywords: OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 666174c4f0f54679907bd239a81c5c369dc09a3d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
Это функция обратного вызова, указанного в вызове [SccSetOption](../extensibility/sccsetoption-function.md) (с помощью параметра `SCC_OPT_NAMECHANGEPFN`) и используется для связи имени изменений, внесенных системы управления версиями подключаемого модуля к Интегрированной среде разработки.  
  
## <a name="signature"></a>Подпись  
  
```cpp  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Параметры  
 pvCallerData  
 [in] Значение пользователя, указанного в предыдущем вызове [SccSetOption](../extensibility/sccsetoption-function.md) (с помощью параметра `SCC_OPT_USERDATA`).  
  
 pszOldName  
 [in] Исходное имя файла.  
  
 pszNewName  
 [in] Назовите файл был переименован в.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Отсутствует.  
  
## <a name="remarks"></a>Примечания  
 При переименовании файла во время операции управления версиями, подключаемый модуль системы управления версиями может уведомить об изменении через этот обратный вызов интегрированной среды разработки.  
  
 Если интегрированная среда разработки не поддерживает этот обратный вызов, он не вызывает [SccSetOption](../extensibility/sccsetoption-function.md) задать его. Если подключаемый модуль не поддерживает этот обратный вызов, он будет возвращать `SCC_E_OPNOTSUPPORTED` из `SccSetOption` работать при попытке задать обратный вызов интегрированной среды разработки.  
  
## <a name="see-also"></a>См. также  
 [Функции обратного вызова, реализуемый интегрированной среды разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)