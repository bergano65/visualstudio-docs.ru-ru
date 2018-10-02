---
title: Привязка сочетания клавиш к пунктам меню | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f661129a4706ce0ac501a5fbad9a7ce5a60e3127
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47563520"
---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Привязка сочетаний клавиш к пунктам меню
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [привязка сочетания клавиш к пунктам меню](https://docs.microsoft.com/visualstudio/extensibility/binding-keyboard-shortcuts-to-menu-items).  
  
Чтобы привязать сочетания клавиш для команды меню, просто добавьте запись vsct-файл для пакета. В этом разделе объясняется, как сопоставить сочетания клавиш для пользовательской кнопки, пункт меню или панели инструментов команды и как применить назначения клавиш в редакторе по умолчанию или ограничить ее специализированный редактор.  
  
 Чтобы назначить сочетания клавиш к существующим элементам меню Visual Studio, см. в разделе [определение и Настройка сочетаний клавиш](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Выбор сочетания клавиш  
 Многие сочетания клавиш уже используются в Visual Studio. Не следует присваивать тот же краткий путь к более чем одной команде, так как повторяющиеся привязки трудно определить, а также может привести к непредсказуемым результатам. Таким образом рекомендуется проверить доступность ярлык до назначения его.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Чтобы проверить доступность сочетания клавиш  
  
1.  В **Сервис / Параметры / Среда** выберите **клавиатуры**.  
  
2.  Убедитесь, что **клавиш в** присваивается **Global**.  
  
3.  В **введите сочетание клавиш** введите сочетание клавиш, которое вы хотите использовать.  
  
     Если сочетание клавиш уже используется в Visual Studio **плитки, в настоящий момент используется** команду, которая в настоящее время вызывает ярлык появится окно.  
  
4.  Попробуйте различные сочетания клавиш, пока не найдете не сопоставлен.  
  
    > [!NOTE]
    >  Сочетания клавиш, нажмите клавиши ALT может открыть меню и не непосредственно выполнить команду. Таким образом **плитки, в настоящий момент используется** поле может быть пустым, при вводе ярлык, который включает в себя ALT. Убедитесь, что ярлык не открывается меню, закрывая **параметры** диалоговое окно и нажав клавиши.  
  
 В следующей процедуре предполагается, что у вас есть существующие VSPackage с командой меню. Если вам нужна помощь, сделать это, рассмотрим [создания расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Чтобы назначить сочетания клавиш для команды  
  
1.  Откройте vsct-файл для пакета.  
  
2.  Создать пустой `<KeyBindings>` разделе после `<Commands>` если его еще нет.  
  
    > [!WARNING]
    >  Дополнительные сведения о привязки клавиш, см. в разделе [сочетание клавиш](../extensibility/keybinding-element.md).  
  
     В `<KeyBindings>` разделе, создайте `<KeyBinding>` запись.  
  
     Задайте `guid` и `id` атрибуты те команды, которую требуется вызвать.  
  
     Задайте `mod1` атрибут **управления**, **Alt**, или **Shift**.  
  
     В разделе сочетания клавиш должен выглядеть следующим образом:  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 Если сочетание клавиш требуется более двух ключей, задайте `mod2` и `key2` атрибуты.  
  
 В большинстве случаев **Shift** не должны использоваться без второй модификатора, поскольку уже ее нажатие вызывает большинство буквенно-цифровых клавиш ввода буквы верхнего регистра или символ.  
  
 Ключ виртуальной коды позволяют специальные ключи, у которых нет символов, связанных с ними, например, функциональные клавиши доступа и **BACKSPACE** ключ. Дополнительные сведения см. в разделе [коды виртуальных ключ](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
 Чтобы сделать команду доступной в Visual Studio редактора, задайте `editor` атрибут `guidVSStd97`.  
  
 Чтобы сделать команду доступной только в пользовательском редакторе, задайте `editor` атрибут имя настраиваемого редактора, созданное [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] шаблона пакета при создании пакета VSPackage, который включает в себя настраиваемого редактора. Значение имени, см. `<Symbols>` раздел `<GuidSymbol>` узел которого `name` атрибута заканчивается на "`editorfactory`.» Это имя настраиваемого редактора.  
  
## <a name="example"></a>Пример  
 В этом примере привязывает сочетание клавиш CTRL + ALT + C для команды с именем `cmdidMyCommand` в пакете с именем `MyPackage`.  
  
```  
<CommandTable>  
. . .  
<Commands>  
. . .  
</Commands>  
<KeyBindings>  
  <KeyBinding guid="guidMyPackageCmdSet" id="cmdidMyCommand"   
      key1="C" mod1="CONTROL" mod2="ALT" editor="guidVSStd97" />  
</KeyBindings>  
. . .  
</CommandTable>  
```  
  
## <a name="example"></a>Пример  
 В этом примере привязывает сочетание клавиш CTL + B для команды с именем `cmdidBold` в проект с именем `TestEditor`. Команда доступна только в пользовательском редакторе, а не в других редакторах.  
  
```xml  
<KeyBinding guid="guidVSStd97" id="cmdidBold" editor="guidTestEditorEditorFactory" key1="B" mod1="Control" />  
```  
  
## <a name="see-also"></a>См. также  
 [Расширение меню и команд](../extensibility/extending-menus-and-commands.md)

