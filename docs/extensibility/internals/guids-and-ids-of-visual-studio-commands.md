---
title: Идентификаторы GUID и идентификаторы команд Visual Studio | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- commands
- id
- command placement
- visual studio command
- guid
ms.assetid: 2ea4bee2-0259-4675-8e65-2023b312b516
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 67c773fcd6afe5953d47e7f563189263d1092444
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49926550"
---
# <a name="guids-and-ids-of-visual-studio-commands"></a>Идентификаторы GUID и идентификаторы Visual Studio команды
Значения GUID и идентификатор команды, добавленные в среде разработки Visual Studio (IDE) определяются в файлах .vsct, установленные как часть Visual Studio SDK. Дополнительные сведения см. в разделе [команды, определенные в интегрированной среде разработки, меню и групп](../../extensibility/internals/ide-defined-commands-menus-and-groups.md).  
  
 Дополнительные сведения о том, как работать с объектами интегрированной среды разработки, которые определены в *.vsct* файлы, см. в разделе [расширить меню и команд](../../extensibility/extending-menus-and-commands.md).  
  
## <a name="find-a-command-definition"></a>Найти определение команды  
 Так как Visual Studio определяет более чем на 1000 команд, нецелесообразно перечислить их все здесь. Вместо этого выполните следующие действия для этого найдите определение команды.  
  
### <a name="to-locate-a-command-definition"></a>Для этого найдите определение команды  
  
1. В Visual Studio, откройте следующие файлы в *< путь установки Visual Studio SDK\>\VisualStudioIntegration\Common\Inc\\*  папки: *SharedCmdDef.vsct*, *ShellCmdDef.vsct*, *VsDbgCmdUsed.vsct*, *Venusmenu.vsct*.  
  
    Большинство команд Visual Studio определяются в *SharedCmdDef.vsct* и *ShellCmdDef.vsct*. *VsDbgCmdUsed.vsct* определяет команды, относящиеся к отладчику, и *Venusmenu.vsct* определяет команды, относящиеся к веб-разработки.  
  
2. Если команда в данный элемент меню, обратите внимание, точный текст пункта меню. Если команда является кнопки на панели инструментов, обратите внимание, текст подсказки, отображаемой при наведении на него.  
  
3. Нажмите клавишу **Ctrl**+**F** открыть **найти** диалоговое окно.  
  
4. В **найти** введите текст, записанный на шаге 2.  
  
5. Убедитесь, что **все открытые документы** отображается в **папка** поле.  
  
6. Нажмите кнопку **Найти далее** переключатель, пока текст выбран в `<Strings>` раздел [элемент Button](../../extensibility/button-element.md).  
  
    `<Button>` Элемент, который команда отображается в — определение команды.  
  
   Когда вы найдете определения команды, можно поместить копию команды на другом меню или панели инструментов, создав [элемент CommandPlacement](../../extensibility/commandplacement-element.md) с тем же установленным `guid` и `id` значения, что команда. Дополнительные сведения см. в разделе [создание повторно используемых групп кнопок](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
### <a name="special-cases"></a>Особые случаи  
 В следующих случаях текст меню или текст подсказки может не совпадать в определение команды.  
  
-   Пунктами меню, включающими подчеркнутый символ, такой как **печати** команды **файл** меню, в котором *P* подчеркнутым.  
  
     Символы символом амперсанда (&) символов в именах элементов меню отображаются как подчеркнутый. Тем не менее *.vsct* файлы записываются в формате XML, которая использует символ амперсанда (&), чтобы указать специальные символы и требует, что необходимо уточнять амперсанд для отображения, как  *&amp;amp;*. Таким образом, в *.vsct* файл, **P**rint команда появляется как  *&amp;amp; Печать*.  
  
-   Команды, имеющие динамический текст, такие как **Сохранить** \<текущее имя файла\>и динамически созданные элементы меню, например элементы на **последние файлы** списка.  
  
     Нет надежного способа для поиска на динамический текст. Вместо этого найдите группу, на котором размещена нужную команду по журналу [меню идентификаторы GUID и идентификаторы Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) или [идентификаторы GUID и идентификаторы Visual Studio панель](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)и выполните поиск по Идентификатору этой группы. Если определение команды не ту группу, что его [родительского элемента](../../extensibility/parent-element.md), поиска *SharedCmdPlace.vsct* и *ShellCmdPlace.vsct* (или  *VsDbgCmdPlace.vsct* для команд отладчика) для `<CommandPlacement>` элемент, который задает родительский объект команды. *SharedCmdPlace.vsct*, *ShellCmdPlace.vsct*, и *VsDbgCmdPlace.vsct* в *\<путь установки Visual Studio SDK\>\ VisualStudioIntegration\Common\Inc\\* папки.  
  
## <a name="see-also"></a>См. также  
 [Команды MenuCommand и OleMenuCommands](../../extensibility/menucommands-vs-olemenucommands.md)   
 [Visual Studio командные файлы table (.vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Справочник по схемам VSCT XML](../../extensibility/vsct-xml-schema-reference.md)
