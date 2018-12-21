---
title: VsgDbg::VsgDbg (конструктор) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 056c5f5e19a4d1e025969aa40ad75f3852b4201b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51781924"
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
 Значение `true` для указания того, что компонент диагностики графики в приложении должен быть подготовлен к активному захвату и записи данных графики; значения `false` для указания того, что в данный момент приложение не должно быть подготовлено к активному захвату и записи данных графики.  
  
## <a name="remarks"></a>Примечания  
 При вызове конструктора с `bDefaultInit` присвоено `true`, имя файла, файла журнала графики, определяется как `DONT_SAVE_VSGLOG_TO_TEMP` и `VSG_DEFAULT_RUN_FILENAME` определены символы препроцессора, прежде чем `vsgcapture.h` включается в вашем приложении.  
  
 При вызове конструктора с параметром `bDefaultInit`, установленным в значение `false`, компонент диагностики графики в приложении может быть подготовлен для активного захвата и записи данных графики позднее с помощью функции `Init`.  
  
## <a name="see-also"></a>См. также  
 [VsgDbg:: ~ VsgDbg (деструктор)](../debugger/vsgdbg-tilde-vsgdbg-destructor.md)   
 [init](../debugger/init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)



