---
title: VSG_NODEFAULT_INSTANCE | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 19c95b0d-9a4d-441f-9ed7-3acb39e67521
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9c7d2263642c2ff8a2c36f274d2c7b80745ed845
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979336"
---
# <a name="vsgnodefaultinstance"></a>VSG_NODEFAULT_INSTANCE
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Определяет своим наличием, нужно ли экземпляр по умолчанию [класс VsgDbg](../debugger/vsgdbg-class.md) класс, который предоставляет программный интерфейс захвата — предоставляется.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
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
