---
title: 'Ошибка: Узел использует IP-адрес | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: daa9ed74df46dd6be66a27d09cbbd7c311e03de4
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793676"
---
# <a name="error-site-uses-ip-address"></a>Ошибка: веб-узел использует IP-адрес
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Эта ошибка возникает, если в отладчике выполняется попытка автоматического присоединения к веб-приложению, которое использует IP-адрес. Это происходит при изменении **Идентификация веб-сайта** для **определенный IP-адрес** в службах IIS.  
  
 Для работы автопривязки необходимо создать проект с определенным IP-адресом вместо имени компьютера. В противном случае имя машины будет заменено отладчиком на имя "localhost". Это вызовет сбой отправки команды службам IIS.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Используйте ручную привязку вместо автопривязки (в меню "Отладка" выберите **присоединение к процессу**).  
  
     —или—  
  
2.  Изменение **идентификация IIS веб-узла** параметр.  
  
## <a name="see-also"></a>См. также  
 [Отладка веб-приложений: ошибки и устранение неполадок](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



