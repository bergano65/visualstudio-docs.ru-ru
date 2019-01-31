---
title: Настройка брандмауэра для удаленной отладки диалоговое окно | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.firewallconfiguration
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Configure Firewall for Remote Debugging dialog box
- remote debugging, configuring firewalls
- firewalls, configuring for remote debugging
ms.assetid: 5dff3393-fdeb-4129-a2f6-31f653107a82
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f4a7346d9398ab9743319661efffdaf3f1f4b89b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55018609"
---
# <a name="configure-firewall-for-remote-debugging-dialog-box"></a>Настройка брандмауэра для удаленной отладки - диалоговое окно
Данное диалоговое окно появляется тогда, когда межсетевой экран Windows блокирует получение отладчиком информации по сети. Для продолжения удаленной отладки в межсетевом экране необходимо создать "отверстие" для отладчика, чтобы тот мог беспрепятственно получать информацию.  
  
> [!CAUTION]
>  Открытие "отверстия" в межсетевом экране может привести к возникновению угроз безопасности компьютера, для блокировки которых предназначен брандмауэр. Открытие "отверстия" для удаленной отладки разблокирует порты 4020 и 4021 в Visual Studio 2015. В других версиях Visual Studio используются другие номера портов. Дополнительные сведения см. в разделе [Remote Debugger Port Assignments](../debugger/remote-debugger-port-assignments.md). Кроме того, это дает отладчику возможность открывать дополнительные порты. Дополнительные сведения см. в разделе [Настройка брандмауэра Windows для удаленной отладки](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Отменить удаленную отладку**  
 Отменяет попытку выполнения удаленной отладки. Параметры безопасности компьютера изменены не будут.  
  
 **Разрешить удаленную отладку c компьютеров в локальной сети (подсеть)**  
 Разрешает выполнение удаленной отладки компьютеров в локальной подсети. Это может привести к открытию уязвимых мест компьютеров локальной подсети, но межсетевой экран по-прежнему будет блокировать информацию, поступающую в данную подсеть извне.  
  
 **Разрешить удаленную отладку с любого компьютера**  
 Разрешает выполнение удаленной отладки компьютеров в любой точке сети. Это наименее безопасный вариант.  
  
## <a name="see-also"></a>См. также раздел  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Remote Debugging](../debugger/remote-debugging.md)  
 [Справочник по пользовательскому интерфейсу отладчика](../debugger/debugging-user-interface-reference.md)