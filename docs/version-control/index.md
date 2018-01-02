---
layout: LandingPage
title: "Управление версиями в Visual Studio | VSTS и Team Foundation Server"
description: "Руководство по началу работы с системами управления версиями в Visual Studio"
keywords: VSTS, TFS, Version Control
author: steved0x
ms.manager: douge
ms.author: sdanie
ms.date: 12/15/2017
ms.topic: article
ms.prod: .net-core
ms.assetid: 2c119a5f-0272-48c0-8d6c-806196944aea
ms.openlocfilehash: 471e0cf7640f07c946e2808621233c6ae20b35c7
ms.sourcegitcommit: f36eb7f989efbdbed0d0a087afea8ffe27d8ca15
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/14/2017
---
# <a name="version-control-in-visual-studio"></a>Управление версиями в Visual Studio

Системы управления версиями позволяют отслеживать изменения в коде по времени. Когда вы вносите изменения, система управления версиями создает моментальный снимок файлов. Этот снимок навсегда сохраняется в системе, благодаря чему вы можете повторно вызвать его в любое время. Visual Studio предоставляет такие системы управления версиями, как [Git](/vsts/git/index) и [TFVC](/vsts/tfvc/index) (система управления версиями Team Foundation). Чтобы выбрать одну из них, см. статью [Choosing the right version control for your project](/vsts/tfvc/comparison-git-tfvc?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json) (Выбор системы управления версиями для вашего проекта).

## <a name="git"></a>Git
Git — наиболее часто используемая система управления версиями на сегодняшний день, которая стремительно становится стандартом в мире систем управления версиями. Это распределенная система управления версиями. Это значит, что репозиторий представляет собой полную локальную копию кода. Полнофункциональные локальные репозитории упрощают работу в автономном режиме или в удаленном расположении. Вы работаете в локальной среде, а затем синхронизируете свою копию репозитория с копией на сервере. Эта парадигма отличается от централизованных систем управления версиями, где клиенты должны синхронизировать код с сервером перед созданием новой версии кода.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="https://www.visualstudio.com/learn-git/">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Сведения о Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/vsts/git/share-your-code-in-git-vs-2017?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Начало работы с Git в Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/vsts/git/tutorial/clone?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/common/i_git-mark.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Клонирование существующего репозитория Git</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>

## <a name="tfvc"></a>TFVC

Подсистема контроля версий Team Foundation (TFVC) — это централизованная система управления версиями. Как правило, члены команды имеют на своих компьютерах разработки только одну версию каждого файла. Исторические данные ведутся только на сервере. Ветви основаны на путях и создаются на сервере.

<ul class="panelContent cardsFTitle">
    <li>
        <a href="/vsts/tfvc/overview">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Сведения о TFVC</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
    <li>
        <a href="/vsts/tfvc/share-your-code-in-tfvc-vs?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Начало работы с TFVC в Visual Studio</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
   <li>
        <a href="/vsts/tfvc/get-code-reviewed-vs?toc=/visualstudio/version-control/toc.json&bc=/vsts/git/breadcrumb/vc/toc.json">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage">
                            <img width="48" height="48" alt="" src="https://docs.microsoft.com/media/logos/logo_visual-studio.svg" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3>Проверка кода</h3>
                    </div>
                </div>
            </div>
        </div>
        </a>
    </li>
</ul>


## <a name="resources"></a>Ресурсы 

- [Книга Pro Git (Git для профессионалов)](https://git-scm.com/book/en/v2)  
- [Переход с централизованной системы управления версиями на Git](https://www.visualstudio.com/learn/centralized-to-git/)  
- [Переход с TFVC на Git](https://www.visualstudio.com/learn/migrate-from-tfvc-to-git/)  

 

