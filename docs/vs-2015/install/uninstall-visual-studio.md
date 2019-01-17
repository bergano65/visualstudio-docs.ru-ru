---
title: Удаление Visual Studio 2015 | Документация Майкрософт
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 985f99afb0f9c0e659586d7878df94bf1b7266c3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822429"
---
# <a name="uninstall-visual-studio"></a>Удаление Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последние версии документации Visual Studio 2017, см. в разделе [удалить Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/uninstall-visual-studio).

Этой странице приведены пошаговые инструкции по удалению Visual Studio 2015, более раннюю версию нашего интегрированного набора средств повышения производительности для разработчиков.

##  <a name="uninstalling"></a>
#### <a name="to-uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Удаление Visual Studio с помощью метода «стандартный» удаления

1. На странице **Программы и компоненты** **панели управления** выберите выпуск продукта, который требуется удалить, и нажмите кнопку **Изменить**.

2. В мастере установки выберите **Удалить**, нажмите кнопку **Да**, а затем следуйте инструкциям мастера.

   Этот стандартный или по умолчанию метод оставит некоторые элементы вашей первой установки Visual Studio, изначально установлена (например, Microsoft .NET Framework, Visual C++ распространяемые компоненты Microsoft, Microsoft SQL Server, и т.д.).   Они остаются установленными, так как многие приложения зависят от их. Тем не менее, если вы хотите удалить и эти элементы, выберите их на **программы и компоненты**, а затем удалите по отдельности.

#### <a name="to-uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Чтобы удалить Visual Studio и всех остальных связанных файлов (то есть удаление практически всех элементов)

1.  Найдите файл .exe, Visual Studio (например, найдите «vs_enterprise.exe»).

    > [!NOTE]
    >  Файл должен находиться во вложенной папке «%programdata%\Package Cache», например: Кэш C:\ProgramData\Package\\\vs_enterprise.exe {37e19555-e88d-4aed-9d42-82d0784d2b79}

2.  Запустите файл .exe с помощью / uninstall/force параметры командной строки.

     Например, запустите ```vs_enterprise.exe /uninstall /force```, который приведет к удалению Visual Studio и большинства основных компонентов, оставленных при удалении по умолчанию. Тем не менее он не удаляет все дополнительное содержимое этой надстройки Visual Studio и расширения можно установить (для примера, обновления Visual Studio и другие дополнительные компоненты).

    > [!TIP]
    > Кроме того, можно использовать "**Total Uninstaller**" удалите все, что Visual Studio или может установить обновления для Visual Studio. То есть любой версии Visual Studio 2013 или более поздней версии. Дополнительные сведения см. в разделе [Visual Studio Uninstaller tool](https://github.com/Microsoft/VisualStudioUninstaller/releases) на сайте GitHub.

#### <a name="to-uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Удаление Visual Studio в автоматическом или в пассивном режиме (то есть удаление из источника)

1.  На компьютере, на котором установлена среда Visual Studio, откройте командную строку Windows.

2.  Введите следующие параметры:

     *DVDRoot* \\< файл установки\> \</quiet&#124;/passive > [/ norestart] / uninstall

#### <a name="to-roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Чтобы выполнить откат до предыдущей версии или выпуска Visual Studio

1. Удалите Visual Studio с помощью любого из методов, перечисленных в этом разделе.

   > [!WARNING]
   >  Удаление текущего выпуска Visual Studio (или обновления для Visual Studio) и последующая установка предыдущего выпуска может не работать должным образом.
   >
   >  Результат зависит от какой версии или выпуска Visual Studio вы установили, установленных версий ее компонентов, установленных продуктов, могут иметь зависимости либо этот выпуск Visual Studio или его компоненты и, наконец, на более ранние версии Visual Studio, вы планируете установить или переустановить.  Из-за все эти переменные стандартного удаления будет часто остаются компоненты, может не работать с версиями или предыдущие версии Visual Studio.
   >
   >  Таким образом, для получения наилучших результатов мы рекомендуем использовать [Visual Studio Uninstaller tool](https://github.com/Microsoft/VisualStudioUninstaller/releases).

2. Установите или переустановите более раннюю версию Visual Studio, который вы хотите использовать.

   Даже если вы установите предыдущую версию Visual Studio, программа установки может по-прежнему пытаться использовать более новую версию или выпуск, если таковой доступен. Дополнительные сведения см. в разделе [как: Установка определенного выпуска Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md) раздела.

## <a name="see-also"></a>См. также раздел
 [Установка Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)