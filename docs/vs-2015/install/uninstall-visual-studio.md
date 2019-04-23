---
title: Удаление Visual Studio 2015 | Документация Майкрософт
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e00ca9212c03d4123259715da157201c06d90f2b
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59667304"
---
# <a name="uninstall-visual-studio"></a>Удаление Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Самая актуальная документация по Visual Studio: [Удаление Visual Studio](/visualstudio/install/uninstall-visual-studio).

На этой странице приведены пошаговые инструкции по удалению Visual Studio 2015, более ранней версии интегрированного набора средств для эффективной работы разработчиков.

## <a name="uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Удаление Visual Studio с помощью стандартного метода удаления

1. На странице **Программы и компоненты** **панели управления** выберите выпуск продукта, который требуется удалить, и нажмите кнопку **Изменить**.

2. В мастере установки выберите **Удалить**, нажмите кнопку **Да**, а затем следуйте инструкциям мастера.

   Этот стандартный или заданный по умолчанию метод оставит некоторые элементы вашей первой изначальной установки Visual Studio (например, Microsoft .NET Framework, распространяемые компоненты Microsoft Visual C++, Microsoft SQL Server и т. д.).   Они не будут удалены, потому что от них зависят многие другие приложения. Однако, если нужно удалить и эти элементы, выберите их на странице **Программы и компоненты**, а затем удалите каждый из них по отдельности.

## <a name="uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Удаление Visual Studio и всех остальных связанных файлов (т. е. удаление практически всех элементов)

1.  Найдите EXE-файл Visual Studio (например, vs_enterprise.exe).

    > [!NOTE]
    > Файл должен находиться во вложенной папке %ProgramData%\Package Cache, например C:\ProgramData\Package Cache\\{37e19555-e88d-4aed-9d42-82d0784d2b79}\vs_enterprise.exe

2.  Запустите EXE-файл с использованием параметров командной строки /uninstall /force.

     Например, выполните ```vs_enterprise.exe /uninstall /force```, чтобы удалить Visual Studio и большинство основных компонентов, оставленных при удалении по умолчанию. Однако таким образом дополнительное содержимое, устанавливаемое с помощью надстроек и расширений Visual Studio (например, обновления Visual Studio и другие дополнительные компоненты) удалено не будет.

    > [!TIP]
    > Кроме того, с помощью средства **Total Uninstaller** можно удалить все элементы, которые могли быть установлены Visual Studio или обновлениями Visual Studio. То есть любой версией Visual Studio 2013 или более поздней. Дополнительные сведения см. на странице [Visual Studio Uninstaller tool](https://github.com/Microsoft/VisualStudioUninstaller/releases) (Средство удаления Visual Studio) на сайте GitHub.

## <a name="uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Удаление Visual Studio в режиме без вывода сообщений или в пассивном режиме (т. е. удаление из источника)

1.  На компьютере, на котором установлена среда Visual Studio, откройте командную строку Windows.

2.  Введите следующие параметры:

     *DVDRoot* \\<Installation File\> \</quiet&#124;/passive> [/norestart]/uninstall

## <a name="roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Откат к предыдущей версии или предыдущему выпуску Visual Studio

1. Удалите Visual Studio с помощью любого из приведенных в этом разделе методов.

   > [!WARNING]
   > Удаление текущего выпуска Visual Studio (или обновления Visual Studio) и последующая установка предыдущего выпуска может выполнятся неправильно.
   >
   > Результат зависит от установленной версии или выпуска Visual Studio, версий установленных компонентов, продуктов, которые могут зависеть от выпуска Visual Studio или ее компонентов, и, наконец, от более ранней версии Visual Studio, которую планируется установить или переустановить.  В связи со всеми этими переменными при стандартном удалении часто остаются компоненты, которые могут не работать с предыдущими версиями или выпусками Visual Studio.
   >
   > Таким образом, для получения наилучших результатов рекомендуется использовать [Visual Studio Uninstaller tool](https://github.com/Microsoft/VisualStudioUninstaller/releases).

2. Установите или переустановите более раннюю версию Visual Studio, которую вы хотите использовать.

   Даже если вы установите предыдущую версию Visual Studio, программа установки может по-прежнему пытаться использовать более новую версию или выпуск, если таковые доступны. Дополнительные сведения см. в статье [Практическое руководство. Установка конкретного выпуска Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md).

## <a name="see-also"></a>См. также

- [Установка Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)