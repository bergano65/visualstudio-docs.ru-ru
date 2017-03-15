---
title: "Привязка сочетания клавиш к пунктам меню | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- keyboard command
- keyboards
- command key
- keyboard shortcuts
- menu items
ms.assetid: 19f483b6-4d3e-424e-9d68-dc129c788e47
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e75976be74d7d0362102a2cbeb32a85d3e612c67
ms.lasthandoff: 02/22/2017

---
# <a name="binding-keyboard-shortcuts-to-menu-items"></a>Привязка сочетания клавиш к пунктам меню
Привязка сочетания клавиш для команды пользовательского меню, просто добавьте запись в файл .vsct для пакета. В этом разделе объясняется, как для сопоставления сочетания клавиш для пользовательской кнопки, меню или команды панели инструментов и по применению клавиатуры в редакторе по умолчанию или ограничить его специализированный редактор.  
  
 Чтобы назначить сочетания клавиш для существующих элементов меню Visual Studio, см. раздел [определение и Настройка сочетаний клавиш](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).  
  
## <a name="choosing-a-key-combination"></a>Выбор сочетания клавиш  
 Многие сочетания клавиш уже используются в Visual Studio. Не следует присваивать того же сочетания для более чем одной команды, поскольку повторяющиеся привязки сложно обнаружить, а также может привести к непредсказуемым результатам. Таким образом рекомендуется проверить доступность ярлык до назначения его.  
  
#### <a name="to-verify-the-availability-of-a-keyboard-shortcut"></a>Чтобы проверить доступность сочетания клавиш  
  
1.  В **Сервис / Параметры / Среда** выберите **клавиатуры**.  
  
2.  Убедитесь, что **клавиш в** равен **Global**.  
  
3.  В **клавиши** введите сочетание клавиш, которое вы хотите использовать.  
  
     Если сочетание клавиш уже используется в Visual Studio **в настоящий момент используется сочетанием** команду, которая в настоящее время вызывает ярлык появится окно.  
  
4.  Попробуйте различные сочетания клавиш, пока не найдете, не сопоставлен.  
  
    > [!NOTE]
    >  Сочетания клавиш, нажмите клавиши ALT может открыть меню и команды выполняются не напрямую. Таким образом **сочетанием в настоящий момент используется** при вводе ярлык, который включает в себя ALT поле может быть пустым. Убедитесь, что ярлык не открыть меню, закрывая **параметры** диалоговое окно и затем нажатия клавиш.  
  
 Следующая процедура предполагает наличие существующего VSPackage с командой меню. Если требуется помощь, взгляните на [создания расширения с командой меню](../extensibility/creating-an-extension-with-a-menu-command.md).  
  
#### <a name="to-assign-a-keyboard-shortcut-to-a-command"></a>Чтобы назначить сочетания клавиш для команды  
  
1.  Откройте файл .vsct для пакета.  
  
2.  Создать пустой `<KeyBindings>` статьи после `<Commands>` если его там еще нет.  
  
    > [!WARNING]
    >  Дополнительные сведения о привязках ключа в разделе [соответствующие клавиши](../extensibility/keybinding-element.md).  
  
     В `<KeyBindings>` статьи, создайте `<KeyBinding>` запись.  
  
     Задайте `guid` и `id` атрибутов для тех, для вызова команды.  
  
     Задайте `mod1` атрибут **управления**, **Alt**, или **Shift**.  
  
     В разделе привязки клавиш должен выглядеть примерно следующим образом:  
  
    ```xml  
    <KeyBindings>  
        <KeyBinding guid="<name of command set>" id="<name of command id>"  
            editor="guidVSStd97" key1="1" mod1="CONTROL"/>  
    </KeyBindings>  
  
    ```  
  
 Если сочетание клавиш требует более двух ключей, установите `mod2` и `key2` атрибуты.  
  
 В большинстве случаев **Shift** не должен использоваться без второй модификатора, поскольку уже ее нажатие вызывает большинство буквенно-цифровые клавиши ввода буквы верхнего регистра или символ.  
  
 Ключ виртуальной коды позволяют открывать специальные ключи, у которых нет символов, связанных с ними, например, функциональные клавиши и **BACKSPACE** ключа. Дополнительные сведения см. в разделе [коды виртуальных ключ](http://go.microsoft.com/fwlink/?LinkID=105932).  
  
 Чтобы сделать команду доступной в Visual Studio редактор, установите `editor` атрибут `guidVSStd97`.  
  
 Чтобы сделать команду доступной только в пользовательском редакторе, установите `editor` атрибуту имя пользовательского редактора, созданное [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] шаблон пакета при создании VSPackage, который включает в себя пользовательский редактор. Чтобы найти имя-значение, найдите `<Symbols>` раздел `<GuidSymbol>` узел которого `name` атрибут заканчивается на «`editorfactory`.» Это имя пользовательского редактора.  
  
## <a name="example"></a>Пример  
 В этом примере привязывает сочетание клавиш CTRL + ALT + C для команды с именем `cmdidMyCommand` в пакет с именем `MyPackage`.  
  
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
