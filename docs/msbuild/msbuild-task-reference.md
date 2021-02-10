---
title: Справочные сведения о задачах MSBuild | Документация Майкрософт
description: Сведения о задачах, которые входят в состав MSBuild и содержат код, выполняемый в процессе сборки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: b3144b27-a426-4259-b8ae-5f7991b202b6
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f26c3c1b8256597c795fa8bcd815fd605f895fa5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878387"
---
# <a name="msbuild-task-reference"></a>Справочник по задачам MSBuild

Задачи содержат код, который выполняется в процессе сборки. Задачи в следующем списке входят в состав MSBuild. После установки рабочей нагрузки C++ станут доступны дополнительные задачи, используемые для создания проектов C++. Дополнительные сведения см. в разделе [Задачи C++](../msbuild/msbuild-tasks-specific-to-visual-cpp.md).

Помимо параметров, перечисленных в подразделах этого раздела, у каждой задачи существуют следующие параметры:

| Параметр | Описание |
|-------------------| - |
| `Condition` | Необязательный параметр `String`.<br /><br /> Выражение `Boolean`, на основании которого механизм MSBuild определяет, будет ли выполняться эта задача. Сведения о поддерживаемых в MSBuild условиях см. в статье об [условиях](../msbuild/msbuild-conditions.md). |
| `ContinueOnError` | Необязательный параметр. Может содержать одно из следующих значений:<br /><br /> -   **WarnAndContinue** или **true**. При сбое задачи последующие задачи в элементе [Target](../msbuild/target-element-msbuild.md) и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как предупреждения.<br />-   **ErrorAndContinue**. При сбое задачи последующие задачи в элементе `Target` и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как ошибки.<br />-   **ErrorAndStop** или **false** (значение по умолчанию). При сбое задачи остальные задачи в элементе `Target` и сборке не выполняются, и считается, что возник сбой всего элемента `Target` и всей сборки.<br /><br /> Версии платформы .NET Framework, предшествовавшие 4.5, поддерживали только значения `true` и `false`.<br /><br /> Дополнительные сведения см. в руководстве по [игнорированию ошибок в задачах](../msbuild/how-to-ignore-errors-in-tasks.md). |

## <a name="in-this-section"></a>В этом разделе

- [Базовый класс Task](../msbuild/task-base-class.md)

 Добавляет несколько параметров в задачи, производные от класса <xref:Microsoft.Build.Utilities.Task>. Не предназначен для непосредственного использования.

- [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md)

 Добавляет несколько параметров в задачи, производные от класса <xref:Microsoft.Build.Tasks.TaskExtension>. Не предназначен для непосредственного использования.

- [Базовый класс ToolTaskExtension](../msbuild/tooltaskextension-base-class.md)

 Добавляет несколько параметров в задачи, производные от класса <xref:Microsoft.Build.Tasks.ToolTaskExtension>. Не предназначен для непосредственного использования.

- [Задача AL (компоновщик сборок)](../msbuild/al-assembly-linker-task.md)

 Создает сборку с манифестом из одного или нескольких файлов, являющихся модулями или файлами ресурсов.

- [AspNetCompiler - задача](../msbuild/aspnetcompiler-task.md)

 Создает оболочку для программы *aspnet_compiler.exe*, которая выполняет предварительную компиляцию приложений ASP.NET.

- [AssignCulture - задача](../msbuild/assignculture-task.md)

 Назначает элементам идентификаторы языка.

- [Задача AssignProjectConfiguration](../msbuild/assignprojectconfiguration-task.md)

 Принимает строки конфигурации списка и назначает их конкретным проектам.

- [Задача AssignTargetPath](../msbuild/assigntargetpath-task.md)

 Принимает список файлов и добавляет атрибуты `<TargetPath>`, если они еще не указаны.

- [CallTarget - задача](../msbuild/calltarget-task.md)

 Вызывает целевой объект в файле проекта.

- [CombinePath - задача](../msbuild/combinepath-task.md)

 Объединяет указанные пути в единый путь.

- [ConvertToAbsolutePath - задача](../msbuild/converttoabsolutepath-task.md)

 Преобразует относительный путь или ссылку в абсолютный путь.

- [Copy - задача](../msbuild/copy-task.md)

 Копирует файлы в новое расположение.

- [CreateCSharpManifestResourceName - задача](../msbuild/createcsharpmanifestresourcename-task.md)

 Создает имя манифеста в стиле C# на основе заданного имени *RESX*-файла или другого ресурса.

- [CreateItem - задача](../msbuild/createitem-task.md)

 Заполняет коллекции элементов входными элементами, позволяя копировать элементы из одного списка в другой.

- [CreateProperty - задача](../msbuild/createproperty-task.md)

 Заполняет свойства входными значениями, позволяя копировать значения из одного свойства или строки в другое свойство или строку.

- [CreateVisualBasicManifestResourceName - задача](../msbuild/createvisualbasicmanifestresourcename-task.md)

 Создает имя манифеста в стиле Visual Basic на основе заданного имени *RESX*-файла или другого ресурса.

- [Задача Csc](../msbuild/csc-task.md)

 Вызывает компилятор Visual C# для создания исполняемых файлов, библиотек динамической компоновки или модулей кода.

- [Delete - задача](../msbuild/delete-task.md)

 Удаляет указанные файлы.

- [Задача DownloadFile](../msbuild/downloadfile-task.md)

 Скачивает файл в заданное расположение.

- [Error - задача](../msbuild/error-task.md)

 Останавливает сборку и регистрирует ошибку в журнале событий на основании вычисленного условного оператора.

- [Exec - задача](../msbuild/exec-task.md)

 Запускает заданную программу или команду с помощью заданных аргументов.

- [FindAppConfigFile - задача](../msbuild/findappconfigfile-task.md)

 Выполняет поиск файла *app.config* (если он имеется) в предоставленных списках.

- [FindInList - задача](../msbuild/findinlist-task.md)

 Выполняет поиск элемента с указанной спецификацией в заданном списке.

- [FindUnderPath - задача](../msbuild/findunderpath-task.md)

 Определяет, какие элементы в указанной коллекции находятся в указанной папке и ее подпапках.

- [FormatUrl - задача](../msbuild/formaturl-task.md)

 Преобразовывает URL-адрес в правильный формат URL-адреса.

- [Задача FormatVersion](../msbuild/formatversion-task.md)

 Добавляет номер редакции к номеру версии.

- [GenerateApplicationManifest - задача](../msbuild/generateapplicationmanifest-task.md)

 Создает манифест приложения ClickOnce или собственный манифест.

- [GenerateBootstrapper - задача](../msbuild/generatebootstrapper-task.md)

 Задача обеспечивает автоматическое обнаружение, скачивание и установку приложения и необходимых для него компонентов.

- [GenerateDeploymentManifest - задача](../msbuild/generatedeploymentmanifest-task.md)

 Создает манифест развертывания ClickOnce.

- [GenerateResource - задача](../msbuild/generateresource-task.md)

 Преобразовывает файлы *TXT* и *RESX* в двоичные файлы *RESOURCES* среды CLR.

- [GenerateTrustInfo - задача](../msbuild/generatetrustinfo-task.md)

 Создает доверие к приложению из базового манифеста и из параметров `TargetZone` и `ExcludedPermissions`.

- [GetAssemblyIdentity - задача](../msbuild/getassemblyidentity-task.md)

 Извлекает идентификаторы сборок из указанных файлов и выводит сведения об удостоверении.

- [Задача GetFileHash](../msbuild/getfilehash-task.md)

 Вычисляет контрольные суммы содержимого файла или набора файлов.

- [GetFrameworkPath - задача](../msbuild/getframeworkpath-task.md)

 Извлекает путь к сборкам .NET Framework.

- [GetFrameworkSdkPath - задача](../msbuild/getframeworksdkpath-task.md)

 Извлекает путь к пакету средств разработки программного обеспечения (SDK) Windows.

- [Задача GetReferenceAssemblyPaths](../msbuild/getreferenceassemblypaths-task.md)

 Возвращает пути к эталонным сборкам для различных версий .NET Framework.

- [LC - задача](../msbuild/lc-task.md)

 Создает файл *LICENSE* из файла *LICX*.

- [MakeDir - задача](../msbuild/makedir-task.md)

 Создает каталоги и при необходимости любые родительские каталоги.

- [Message - задача](../msbuild/message-task.md)

 Записывает сообщения в журнал в процессе сборки.

- [Move - задача](../msbuild/move-task.md)

 Перемещает файлы в новое расположение.

- [MSBuild - задача](../msbuild/msbuild-task.md)

 Выполняет сборку проектов MSBuild из другого проекта MSBuild.

- [ReadLinesFromFile - задача](../msbuild/readlinesfromfile-task.md)

 Считывает список элементов из текстового файла.

- [RegisterAssembly - задача](../msbuild/registerassembly-task.md)

 Считывает метаданные из указанной сборки и добавляет в реестр необходимые записи.

- [Задача RemoveDir](../msbuild/removedir-task.md)

 Удаляет указанные каталоги и все содержащиеся в них файлы и подкаталоги.

- [RemoveDuplicates - задача](../msbuild/removeduplicates-task.md)

 Удаляет повторяющиеся элементы из указанной коллекции элементов.

- [RequiresFramework35SP1Assembly - задача](../msbuild/requiresframework35sp1assembly-task.md)

 Определяет, требуется ли для приложения платформа .NET Framework 3.5 SP1.

- Задача ResGen

 Является устаревшей. Используйте [задачу GenerateResource](../msbuild/generateresource-task.md) для преобразования файлов *TXT* и *RESX* в двоичные файлы *RESOURCES* среды CLR и обратно.

- [ResolveAssemblyReference - задача](../msbuild/resolveassemblyreference-task.md)

 Определяет все сборки, которые зависят от указанных сборок.

- [Задача ResolveComReference](../msbuild/resolvecomreference-task.md)

 Задача принимает список из одной или нескольких библиотек типов или файлов *TLB* и определяет расположение этих библиотек на диске.

- [ResolveKeySource - задача](../msbuild/resolvekeysource-task.md)

 Определяет источник ключа строгого имени.

- [ResolveManifestFiles - задача](../msbuild/resolvemanifestfiles-task.md)

 Разрешает следующие элементы в процессе сборки в файлы для создания манифеста: элементы сборки, зависимости, вспомогательные элементы, содержимое, отладочные символы и документация.

- [ResolveNativeReference - задача](../msbuild/resolvenativereference-task.md)

 Разрешает машинные ссылки.

- [ResolveNonMSBuildProjectOutput - задача](../msbuild/resolvenonmsbuildprojectoutput-task.md)

 Определяет выходные файлы для ссылок на проекты, не относящихся к MSBuild.

- [SGen - задача](../msbuild/sgen-task.md)

 Создает сборку сериализации XML для типов в указанной сборке.

- [SignFile - задача](../msbuild/signfile-task.md)

 Подписывает указанный файл с помощью заданного сертификата.

- [Touch - задача](../msbuild/touch-task.md)

 Задает время доступа и изменения файлов.

- [UnregisterAssembly - задача](../msbuild/unregisterassembly-task.md)

 Отменяет регистрацию указанных сборок для целей COM-взаимодействия.

- [Задача Unzip](../msbuild/unzip-task.md)

 Распаковывает *ZIP-архив* в заданное расположение.

- [UpdateManifest - задача](../msbuild/updatemanifest-task.md)

 Обновляет выбранные свойства в манифесте и выполняет повторное подписание.

- [Задача Vbc](../msbuild/vbc-task.md)

 Вызывает компилятор Visual Basic для создания исполняемых файлов, библиотек динамической компоновки или модулей кода.

- [Задача VerifyFileHash](../msbuild/verifyfilehash-task.md)

 Проверяет, что файл соответствует ожидаемому хэшу файла.

- [Warning - задача](../msbuild/warning-task.md)

 Регистрирует в журнале предупреждение в процессе сборки на основе вычисленного условного оператора.

- [WriteCodeFragment - задача](../msbuild/writecodefragment-task.md)

 Создает временный файл кода с использованием созданного указанного фрагмента кода. Не удаляет этот файл.

- [WriteLinesToFile - задача](../msbuild/writelinestofile-task.md)

 Записывает указанные элементы в указанный текстовый файл.

- [XmlPeek - задача](../msbuild/xmlpeek-task.md)

 Возвращает из XML-файла значения, указанные в запросе XPath.

- [XmlPoke - задача](../msbuild/xmlpoke-task.md)

 Задает в XML-файле значения, указанные в запросе XPath.

- [XslTransformation - задача](../msbuild/xsltransformation-task.md)

 Преобразует входные данные XML с помощью *XSLT* или скомпилированного XSLT и выводит результат на устройство вывода или в выходной файл.

- [Задача ZipDirectory](../msbuild/zipdirectory-task.md)

 Создает *ZIP-архив* из содержимого каталога.

## <a name="see-also"></a>См. также

- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Написание задач](../msbuild/task-writing.md)
- [Задачи](../msbuild/msbuild-tasks.md)
