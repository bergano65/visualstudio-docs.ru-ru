---
title: VsgDbg::VsgDbg (конструктор) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3bd179aea7d961df6145b7af2f074927fcdc3e3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157441"
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (конструктор)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Создает экземпляр класса `VsgDbg` с подготовкой или без подготовки компонента диагностики графики в приложении для активного захвата и записи данных графики по умолчанию, в зависимости от заданного логического параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bDefaultInit`  
 `true` чтобы указать, что компонент диагностики графики в приложении должен быть подготовлен для активной записи и записи графических данных; `false` чтобы указать, что приложение не должно быть подготовлено к активному сбору и записи графических данных в данный момент.  
  
## <a name="remarks"></a>Примечания  
 При вызове конструктора с параметром `bDefaultInit`, установленным в значение `true`, имя файла журнала графики зависит от того, как определены символы препроцессора `DONT_SAVE_VSGLOG_TO_TEMP` и `VSG_DEFAULT_RUN_FILENAME` до включения `vsgcapture.h` в приложение.  
  
 При вызове конструктора с параметром `bDefaultInit`, установленным в значение `false`, компонент диагностики графики в приложении может быть подготовлен для активного захвата и записи данных графики позднее с помощью функции `Init`.  
  
## <a name="see-also"></a>См. также:  
 [VsgDbg:: ~ VsgDbg (деструктор)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [Ini](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)
