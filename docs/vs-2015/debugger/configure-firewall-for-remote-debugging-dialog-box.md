---
title: Настройка брандмауэра для удаленной отладки диалоговое окно | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91b0d7ee490b4e081a264c41b4fe85de07cb637b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63437810"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Настройка брандмауэра для удаленной отладки - диалоговое окно
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Данное диалоговое окно появляется тогда, когда межсетевой экран Windows блокирует получение отладчиком информации по сети. Для продолжения удаленной отладки в межсетевом экране необходимо создать "отверстие" для отладчика, чтобы тот мог беспрепятственно получать информацию.  
  
> [!CAUTION]
> Открытие "отверстия" в межсетевом экране может привести к возникновению угроз безопасности компьютера, для блокировки которых предназначен брандмауэр. Открытие "отверстия" для удаленной отладки разблокирует порты 4020 и 4021 в Visual Studio 2015. В других версиях Visual Studio используются другие номера портов. Дополнительные сведения см. в разделе [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Кроме того, это дает отладчику возможность открывать дополнительные порты. Дополнительные сведения см. в разделе [Настройка брандмауэра Windows для удаленной отладки](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Отменить удаленную отладку**  
 Отменяет попытку выполнения удаленной отладки. Параметры безопасности компьютера изменены не будут.  
  
 **Разрешить удаленную отладку c компьютеров в локальной сети (подсеть)**  
 Разрешает выполнение удаленной отладки компьютеров в локальной подсети. Это может привести к открытию уязвимых мест компьютеров локальной подсети, но межсетевой экран по-прежнему будет блокировать информацию, поступающую в данную подсеть извне.  
  
 **Разрешить удаленную отладку с любого компьютера**  
 Разрешает выполнение удаленной отладки компьютеров в любой точке сети. Это наименее безопасный вариант.  
  
## <a name="see-also"></a>См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Настройка инструментов удаленной отладки на устройстве](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)   
 [Справочник по пользовательскому интерфейсу отладчика](../debugger/debugging-user-interface-reference.md)
