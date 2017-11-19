---
title: "Ошибка: Удаленный компьютер не отображается в диалоговом окне удаленных подключений | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: "2"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e0d8c28f2be735ebb1063715e19a6f2cae55753a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Ошибка "Удаленный компьютер не отображается в диалоговом окне удаленных подключений"
Если удаленный компьютер не отображается в диалоговом окне "Удаленные подключения", проверьте указанные ниже наиболее вероятные причины.  
  
 Если вы используете режим совместимости управляемого кода, обратитесь к документации по Visual Studio 2010: [Устранение неполадок удаленной отладки в Visual Studio 2010](https://msdn.microsoft.com/en-us/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Распространенные причины этой ошибки  
  
-   Удаленный компьютер находится в другой подсети. Чтобы устранить эту проблему, вручную введите имя или IP-адрес компьютера в окне "Описатель".  
  
-   Удаленный отладчик не запущен на удаленном компьютере. Чтобы устранить эту проблему, запустите удаленный отладчик.  
  
-   Брандмауэр блокирует обмен данными между Visual Studio и удаленным компьютером. Чтобы устранить эту проблему, настройте брандмауэр, разрешив обмен данными между Visual Studio и удаленным отладчиком (msvsmon).  
  
-   Антивирусная программа блокирует обмен данными между Visual Studio и удаленным компьютером. Чтобы устранить эту проблему, настройте антивирусную программу, разрешив обмен данными между Visual Studio и удаленным отладчиком (msvsmon).  
  
## <a name="see-also"></a>См. также  
 [Удаленная отладка](../debugger/remote-debugging.md)