---
title: Настройка брандмауэра для удаленной отладки диалоговое окно | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26e53e4573de1fb80d33b387e97b6ddd23b54bbb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573212"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Настройка брандмауэра для удаленной отладки - диалоговое окно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Настройка брандмауэра для удаленной отладки диалоговое окно](https://docs.microsoft.com/visualstudio/debugger/configure-firewall-for-remote-debugging-dialog-box).  
  
Данное диалоговое окно появляется тогда, когда межсетевой экран Windows блокирует получение отладчиком информации по сети. Для продолжения удаленной отладки в межсетевом экране необходимо создать "отверстие" для отладчика, чтобы тот мог беспрепятственно получать информацию.  
  
> [!CAUTION]
>  Открытие "отверстия" в межсетевом экране может привести к возникновению угроз безопасности компьютера, для блокировки которых предназначен брандмауэр. Открытие "отверстия" для удаленной отладки разблокирует порты 4020 и 4021 в Visual Studio 2015. В других версиях Visual Studio используются другие номера портов. Дополнительные сведения см. в разделе [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Кроме того, это дает отладчику возможность открывать дополнительные порты. Дополнительные сведения см. в разделе [Настройка брандмауэра Windows для удаленной отладки](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Отменить удаленную отладку**  
 Отменяет попытку выполнения удаленной отладки. Параметры безопасности компьютера изменены не будут.  
  
 **Разрешить удаленную отладку с компьютеров в локальной сети (подсеть)**  
 Разрешает выполнение удаленной отладки компьютеров в локальной подсети. Это может привести к открытию уязвимых мест компьютеров локальной подсети, но межсетевой экран по-прежнему будет блокировать информацию, поступающую в данную подсеть извне.  
  
 **Разрешить удаленную отладку с любого компьютера**  
 Разрешает выполнение удаленной отладки компьютеров в любой точке сети. Это наименее безопасный вариант.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Настройка инструментов удаленной отладки на устройстве](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Справочник по пользовательскому интерфейсу отладчика](../debugger/debugging-user-interface-reference.md)



