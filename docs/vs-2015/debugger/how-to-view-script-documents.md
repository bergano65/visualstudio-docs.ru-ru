---
title: 'Практическое: просмотр документов скриптов | Документация Майкрософт'
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
helpviewer_keywords:
- Script Explorer
ms.assetid: 8b621e53-4508-4b4a-9995-70995b0b9ac8
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0ede19ada6509bd4473ac2455fbe6cd9fdf5ec8b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735695"
---
# <a name="how-to-view-script-documents"></a>Практическое руководство. Просмотр документов скриптов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В более ранних версиях [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] клиентские файлы скриптов, созданные из серверных скриптов, появлялись в окне обозревателя скриптов. Окно обозревателя скриптов часто было скрыто, так что доступность клиентского скрипта была не всегда очевидна.  
  
 В [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] файлы клиентских скриптов, созданные из серверных скриптов, отображаются в обозревателе решений, который по умолчанию отображается. Окно обозревателя скриптов больше не используется.  
  
 Клиентские файлы скриптов отображаются только в режиме отладки или режиме приостановки. Они отображаются в **документы скриптов** узла.  
  
 Серверные файлы скриптов отображаются всегда. Они отображаются в  **\<путь веб-сайта >** узла. Имя узла выглядит следующим образом: `c:\...\Website2\`  
  
### <a name="to-view-a-server-side-script-document"></a>Просмотр документа серверного скрипта  
  
1.  В **обозревателе решений**откройте  **\<путь веб-сайта >** узла.  
  
2.  Дважды щелкните имя файла скрипта, который нужно просмотреть.  
  
     Серверная часть скрипта откроется в окне исходного кода.  
  
### <a name="to-view-a-client-side-script-document"></a>Просмотр документа клиентского скрипта  
  
1.  В **обозревателе решений**откройте **документы скриптов** узла.  
  
2.  Дважды щелкните имя файла скрипта, который нужно просмотреть.  
  
     Клиентская часть скрипта откроется в окне исходного кода.  
  
## <a name="see-also"></a>См. также  
 [Просмотр данных в отладчике](../debugger/viewing-data-in-the-debugger.md)



