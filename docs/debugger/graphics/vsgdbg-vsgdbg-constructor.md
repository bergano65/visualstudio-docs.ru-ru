---
title: "VsgDbg::VsgDbg (конструктор) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 670651e6-5e79-4845-b0c2-671beb7055a8
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7231e0cc5c9d5946fabe504c16813ea47b24bdbc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="vsgdbgvsgdbg-constructor"></a>VsgDbg::VsgDbg (конструктор)
Создает экземпляр класса `VsgDbg` с подготовкой или без подготовки компонента диагностики графики в приложении для активного захвата и записи данных графики по умолчанию, в зависимости от заданного логического параметра.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
VsgDbg(  
  bDefaultInit  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `bDefaultInit`  
 Значение `true` для указания того, что компонент диагностики графики в приложении должен быть подготовлен к активному захвату и записи данных графики; значения `false` для указания того, что в данный момент приложение не должно быть подготовлено к активному захвату и записи данных графики.  
  
## <a name="remarks"></a>Примечания  
 При вызове конструктора с `bDefaultInit` значение `true`, имя файла журнала графики, определяется как `DONT_SAVE_VSGLOG_TO_TEMP` и `VSG_DEFAULT_RUN_FILENAME` перед определены символы препроцессора `vsgcapture.h` включается в вашем приложении.  
  
 При вызове конструктора с параметром `bDefaultInit`, установленным в значение `false`, компонент диагностики графики в приложении может быть подготовлен для активного захвата и записи данных графики позднее с помощью функции `Init`.  
  
## <a name="see-also"></a>См. также  
 [VsgDbg:: ~ VsgDbg (деструктор)](vsgdbg-tilde-vsgdbg-destructor.md)   
 [Init](init.md)   
 [DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)   
 [VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)