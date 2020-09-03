---
title: VsgDbg::~VsgDbg (деструктор) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0ae3dd206953e728175f4479920861295feae00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200292"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (деструктор)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Уничтожает экземпляр класса `VsgDbg`. В случае интенсивной записи графических сведений файл журнала графики завершается и закрывается, а ресурсы, которые использовались при активном захвате графических данных, освобождаются.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>См. также:  
 [VsgDbg::VsgDbg (конструктор)](../debugger/vsgdbg-vsgdbg-constructor.md)
