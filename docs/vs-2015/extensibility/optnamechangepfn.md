---
title: ОПТНАМЕЧАНЖЕПФН | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- OPTNAMECHANGEPFN
helpviewer_keywords:
- OPTNAMECHANGEPFN callback function
ms.assetid: 147303f3-c7f1-438a-81b7-db891ea3d076
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4969dff811b6517c0274a35884703a9dc0c693cb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194102"
---
# <a name="optnamechangepfn"></a>OPTNAMECHANGEPFN
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это функция обратного вызова, указанная в вызове [скксетоптион](../extensibility/sccsetoption-function.md) (с использованием параметра `SCC_OPT_NAMECHANGEPFN` ) и используемая для передачи изменений имени, сделанных подключаемым модулем системы управления версиями, обратно в интегрированную среду разработки.  
  
## <a name="signature"></a>Подпись  
  
```cpp#  
typedef void (*OPTNAMECHANGEPFN)(  
   LPVOID pvCallerData,  
   LPCSTR pszOldName,  
   LPCSTR pszNewName  
);  
```  
  
## <a name="parameters"></a>Параметры  
 пвкаллердата  
 окне Значение пользователя, указанное в предыдущем вызове [скксетоптион](../extensibility/sccsetoption-function.md) (параметр using `SCC_OPT_USERDATA` ).  
  
 псзолднаме  
 окне Исходное имя файла.  
  
 псзневнаме  
 окне Имя, в которое был переименован файл.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Нет.  
  
## <a name="remarks"></a>Remarks  
 Если файл переименовывается во время операции системы управления версиями, подключаемый модуль системы управления версиями может уведомлять интегрированную среду разработки об изменении имени через этот обратный вызов.  
  
 Если интегрированная среда разработки не поддерживает этот обратный вызов, она не будет вызывать [скксетоптион](../extensibility/sccsetoption-function.md) , чтобы указать его. Если подключаемый модуль не поддерживает этот обратный вызов, он будет возвращен `SCC_E_OPNOTSUPPORTED` из функции, `SccSetOption` когда интегрированная среда разработки попытается установить обратный вызов.  
  
## <a name="see-also"></a>См. также:  
 [Функции обратного вызова, реализованные интегрированной средой разработки](../extensibility/callback-functions-implemented-by-the-ide.md)   
 [SccSetOption](../extensibility/sccsetoption-function.md)
