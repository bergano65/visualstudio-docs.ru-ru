---
title: Отладка элемента управления ActiveX с привязкой к данным | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- data-bound controls, ActiveX
- ActiveX controls, debugging
- controls [Visual Studio], ActiveX
ms.assetid: 9f6e1f00-e25b-48a9-8484-7e67a1232461
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 45a2f6e022c753b0fe543f2265c7ac1961fd474a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58978536"
---
# <a name="debugging-a-data-bound-activex-control"></a>Отладка элемента управления ActiveX с привязкой данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При разработке элемента управления ActiveX, который будет привязан к элементу управления источником данных, можно создавать собственное приложение контейнера и использовать этот контейнер в сеансе отладки.  
  
 Например, создайте диалоговое приложение MFC и поместите элемент управления источником данных и свой элемент управления с привязкой данных в диалоговом окне. Это MFC-приложение можно будет использовать для тестирования во время выполнения и в качестве исполняемого контейнера для отладки элемента управления ActiveX с привязкой данных.  
  
## <a name="using-the-test-container"></a>Использование тестового контейнера  
 Если нужен контейнер, который можно легко изменять для поддержки различных интерфейсов элемента управления или контейнера, используйте тестовый контейнер элемента управления ActiveX в качестве исполняемого во время сеанса отладки. В тестовом контейнере элемента управления ActiveX выберите **Параметры** из меню **Контейнер** для включения различных интерфейсов. Дополнительные сведения см. в разделе [тестирование свойств и событий с использованием тестового контейнера](http://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917).  
  
 В случае необходимости захода в код контейнера во время отладки используйте отладочную версию контейнера или используйте отладочную версию тестового контейнера элемента управления ActiveX. Дополнительные сведения см. в разделе [TSTCON образца: Тестовый контейнер элементов управления ActiveX](http://msdn.microsoft.com/72fa40ef-27d3-400c-813f-10b03236e600).  
  
## <a name="see-also"></a>См. также  
 [Отладка COM и ActiveX](../debugger/com-and-activex-debugging.md)   
 [Элементы управления ActiveX](http://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)
