---
title: "VSG_NODEFAULT_INSTANCE | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 7f94aa50908097b161929e51f260d3bcc058bd5a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
Определяет своим наличием, нужно ли экземпляр по умолчанию [класс VsgDbg](vsgdbg-class.md) класс, который предоставляет программный интерфейс захвата — предоставляется.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
#define VSG_NODEFAULT_INSTANCE  
```  
  
## <a name="value"></a>Значение  
 Символ препроцессора, который своим наличием или отсутствием определяет, предоставляется ли экземпляр по умолчанию класса `VsgDbg`. Если этот символ определен, экземпляр по умолчанию класса `VsgDbg` не предоставляется; в противном случае экземпляр по умолчанию предоставляется и инициализируется до начала работы программы.  
  
 Программный интерфейс захвата предоставляется посредством указателя с глобальной областью видимости — `g_pVsgDbg`.  
  
```  
VsgDbg *g_pVsgDbg;  
```  
  
## <a name="remarks"></a>Примечания  
 Экземпляра по умолчанию обычно достаточно, но для использования программного интерфейса захвата внутри библиотеки DLL, когда устройство D3D было создано вне библиотеки DLL, необходимо создать собственный экземпляр класса `VsgDbg` и управлять им. Если вы управляете собственным интерфейсом к программируемому API захвата подобным образом, во избежание дополнительных затрат на обработку отключите экземпляр по умолчанию, определив `VSG_NODEFAULT_INSTANCE`.  
  
 Если экземпляр по умолчанию не отключен, он автоматически инициализируется до начала работы программы и автоматически уничтожается при ее завершении. Инициализировать или уничтожать этот экземпляр явно нет необходимости.  
  
 Чтобы отключить экземпляр по умолчанию, необходимо определить `VSG_NODEFAULT_INSTANCE` перед включением `vsgcapture.h` в программе.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как отключить экземпляр по умолчанию:  
  
```  
// Define VSG_NODEFAULT_INSTANCE before including vsgcapture.h  
#define VSG_NODEFAULT_INSTANCE  
  
#include <vsgcapture.h>  
```