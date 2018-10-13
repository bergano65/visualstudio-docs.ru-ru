---
title: 'Ошибка: Брандмауэр на локальном компьютере | Документация Майкрософт'
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
- vs.debug.error.firewall.localmachine
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: ab60dda9-7934-4891-aa2f-001380d2ed83
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cbca2e944e7313e54fd469dd41774f40931ee3d2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49245353"
---
# <a name="error-firewall-on-local-machine"></a>Ошибка: брандмауэр на локальном компьютере
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Брандмауэр подключения к интернету на локальном компьютере, с которого запускается Visual Studio, не настроен так, чтобы была доступна удаленная отладка. Для удаленной отладки управляемого или машинного кода с транспортом по умолчанию, порт TCP 135 должен быть открыт для трафика DCOM. Необходимо открыть общий доступ к файлам и принтерам, и файл devenv.exe должен быть добавлен в список исключений. Возможно также потребуется открыть некоторые порты IPSec.  
  
 Дополнительные сведения см. в разделе [задать удаленных инструментов на устройстве](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).



