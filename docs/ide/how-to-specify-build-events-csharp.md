---
title: Практическое руководство. Указание событий сборки (C#)
description: Узнайте, как использовать события сборки для указания команд, которые выполняются до начала сборки или после ее завершения.
ms.custom: SEO-VS-2020
ms.date: 03/21/2019
ms.technology: vs-ide-compile
ms.topic: how-to
helpviewer_keywords:
- pre-build events
- events [Visual Studio], builds
- post-build events
- build events [Visual Studio]
- builds [Visual Studio], events
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e1ea031391b93d571b9f34ad820f1a6957dab242
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869249"
---
# <a name="how-to-specify-build-events-c"></a>Практическое руководство. Указание событий сборки (C#)

Используйте события сборки для указания команд, которые выполняются до начала сборки или после ее завершения. События сборки запускаются, только если сборка успешно достигает этих точек в процессе сборки.

При сборке проекта события перед сборкой добавляются в файл *PreBuildEvent.bat*, а события после сборки — в файл *PostBuildEvent.bat*. Если вы хотите обеспечить проверку ошибок, добавьте собственные команды проверки ошибок в шаги сборки.

## <a name="specify-a-build-event"></a>Указание события сборки

1. В **обозревателе решений** выберите проект, для которого необходимо задать событие сборки.

2. В меню **Проект** выберите **Свойства**.

3. Откройте вкладку **События построения**.

4. В поле **Командная строка события перед сборкой** укажите синтаксис события сборки.

   > [!NOTE]
   > События перед сборкой не выполняются, если проект актуален и сборка не запускается.

5. В поле **Командная строка события после сборки** укажите синтаксис события сборки.

   > [!NOTE]
   > Добавьте оператор `call` перед всеми командами после сборки, запускающими *BAT*-файлы. Например, `call C:\MyFile.bat` или `call C:\MyFile.bat call C:\MyFile2.bat`.

6. В поле **Выполнить событие после сборки** укажите при каких условиях должно выполняться событие после сборки.

   > [!NOTE]
   > Чтобы добавить длинный синтаксис или выбрать макросы сборки из диалогового окна [Командная строка события "После построения" или "Командная строка события "До построения""](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), нажмите кнопку с многоточием (**...**) для отображения поля редактирования.

   Синтаксис события сборки может включать любую команду, допустимую в командной строке или в *BAT*-файле. Для имени пакетного файла необходимо указать префикс `call`, чтобы гарантировать выполнение всех последующих команд.

   > [!NOTE]
   > Если событие перед сборкой или после сборки завершается ошибкой, можно прервать сборку, задав завершение действия события с кодом, отличным от нуля (0), что означает успешное выполнение действия.

## <a name="example"></a>Пример

В следующей процедуре показано, как задать минимальную версию операционной системы в манифесте приложения с помощью команды *EXE*, вызываемой из события после сборки (файл *exe.manifest* в каталоге проекта). Минимальная версия операционной системы — число из четырех частей, например 4.10.0.0. Чтобы задать минимальную версию операционной системы, команда изменит раздел `<dependentOS>` манифеста:

```xml
<dependentOS>
   <osVersionInfo>
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   </osVersionInfo>
</dependentOS>
```

### <a name="create-an-exe-command-to-change-the-application-manifest"></a>Создание команды EXE для изменения манифеста приложения

1. Создайте проект **Консольное приложение** для команды. Назовите проект **ChangeOSVersionCS**.

2. В *Program.cs* добавьте следующую строку для других директив `using` в верхней части файла:

   ```csharp
   using System.Xml;
   ```

3. В пространстве имен `ChangeOSVersionCS` замените реализацию класса `Program` следующим кодом:

   ```csharp
   class Program
   {
      /// <summary>
      /// This function sets the minimum operating system version for a ClickOnce application.
      /// </summary>
      /// <param name="args">
      /// Command Line Arguments:
      /// 0 - Path to application manifest (.exe.manifest)
      /// 1 - Version of OS
      ///</param>
      static void Main(string[] args)
      {
         string applicationManifestPath = args[0];
         Console.WriteLine("Application Manifest Path: " + applicationManifestPath);

         // Get version name.
         Version osVersion = null;
         if (args.Length >=2 ){
            osVersion = new Version(args[1]);
         }else{
            throw new ArgumentException("OS Version not specified.");
         }
         Console.WriteLine("Desired OS Version: " + osVersion.ToString());

         XmlDocument document;
         XmlNamespaceManager namespaceManager;
         namespaceManager = new XmlNamespaceManager(new NameTable());
         namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");
         namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");

         document = new XmlDocument();
         document.Load(applicationManifestPath);

         string baseXPath;
         baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";

         // Change minimum required operating system version.
         XmlNode node;
         node = document.SelectSingleNode(baseXPath, namespaceManager);
         node.Attributes["majorVersion"].Value = osVersion.Major.ToString();
         node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();
         node.Attributes["buildNumber"].Value = osVersion.Build.ToString();
         node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();

         document.Save(applicationManifestPath);
      }
   }
   ```

   Команда принимает два аргумента: путь к манифесту приложения (то есть папка, в которой в процессе сборки создается манифест, обычно *Projectname.publish*) и новую версию операционной системы.

4. Создайте проект.

5. Скопируйте файл *EXE* в каталог, например *C:\TEMP\ChangeOSVersionVB.exe*.

Затем вызовите эту команду в событии после сборки для изменения манифеста приложения.

### <a name="invoke-a-post-build-event-to-modify-the-application-manifest"></a>Вызов события после сборки для изменения манифеста приложения

1. Создайте проект **Приложение Windows Forms** с именем **CSWinApp**.

2. Выберите проект в **обозревателе решений**, а затем в меню **Проект** выберите пункт **Свойства**.

3. В **конструкторе проектов** найдите страницу **Публикация** и для параметра **Расположение публикации** задайте значение *C:\TEMP*.

4. Опубликуйте проект, щелкнув **Опубликовать сейчас**.

   Создается файла манифеста, который сохраняется в каталоге *C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest*. Чтобы просмотреть манифест, щелкните правой кнопкой мыши файл и выберите пункт **Открыть с помощью**, затем выберите **Выбрать программу из списка** и щелкните **Блокнот**.

   Найдите в файле элемент `<osVersionInfo>`. Например, версия может быть следующей:

   ```xml
   <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />
   ```

5. Вернитесь в **конструктор проектов**, перейдите на вкладку **События сборки** и выберите **Изменить событие "После сборки"**.

6. В **командной строке события после сборки** введите следующую команду:

   `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`

   При сборке проекта выполнение этой команды приводит к изменению минимальной версии операционной системы в манифесте приложения на 5.1.2600.0.

   Так как макрос `$(TargetPath)` выражает полный путь к создаваемому исполняемому файлу, файл `$(TargetPath).manifest` будет указывать манифест приложения, созданный в каталоге *bin*. При публикации этот манифест копируется в заданное ранее расположение публикаций.

7. Опубликуйте проект еще раз.

   Версия манифеста должна иметь следующий вид:

   ```xml
   <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />
   ```

## <a name="see-also"></a>См. также раздел

- Сведения о [странице "События сборки" в конструкторе проектов (C#)](../ide/reference/build-events-page-project-designer-csharp.md)
- Сведения о [диалоговых окнах "Командная строка события перед сборкой" и "Командная строка события после сборки"](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)
- [Практическое руководство. Указание событий сборки (Visual Basic)](../ide/how-to-specify-build-events-visual-basic.md)
- [Компиляция и сборка](../ide/compiling-and-building-in-visual-studio.md)
