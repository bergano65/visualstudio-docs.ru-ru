---
title: 'Ошибка: Удаленный компьютер не отображается в диалоговом окне удаленных подключений | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5fd98a5b-2cf3-4438-8b0f-6f1a742a62ce
caps.latest.revision: 5
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 929072304e462e08a45a29c84ab9ce1e20043c49
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51739622"
---
# <a name="error-remote-machine-does-not-appear-in-a-remote-connections-dialog"></a>Ошибка "Удаленный компьютер не отображается в диалоговом окне удаленных подключений"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Если удаленный компьютер не отображается в диалоговом окне "Удаленные подключения", проверьте указанные ниже наиболее вероятные причины.  
  
 Если вы используете режим совместимости управляемого кода, обратитесь к документации по Visual Studio 2010: [Устранение неполадок удаленной отладки в Visual Studio 2010](https://msdn.microsoft.com/library/2ys11ead\(v=vs.100\).aspx) .  
  
### <a name="common-causes-for-this-error"></a>Распространенные причины этой ошибки  
  
-   Удаленный компьютер находится в другой подсети. Чтобы устранить эту проблему, вручную введите имя или IP-адрес компьютера в окне "Описатель".  
  
-   Удаленный отладчик не запущен на удаленном компьютере. Чтобы устранить эту проблему, запустите удаленный отладчик.  
  
-   Брандмауэр блокирует обмен данными между Visual Studio и удаленным компьютером. Чтобы устранить эту проблему, настройте брандмауэр, разрешив обмен данными между Visual Studio и удаленным отладчиком (msvsmon).  
  
-   Антивирусная программа блокирует обмен данными между Visual Studio и удаленным компьютером. Чтобы устранить эту проблему, настройте антивирусную программу, разрешив обмен данными между Visual Studio и удаленным отладчиком (msvsmon).  
  
## <a name="see-also"></a>См. также  
 [Настройка инструментов удаленной отладки в устройстве](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)



