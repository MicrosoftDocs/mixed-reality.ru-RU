---
title: Пишущий инструкции
description: Участие в работе в Windows Mixed Reality документации.
author: mattwojo
ms.author: mattwoj
ms.date: 03/21/2018
ms.topic: article
ms.openlocfilehash: c110b549603f42ec03fd6c0dc8df7bf70ba5ba9f
ms.sourcegitcommit: 384b0087899cd835a3a965f75c6f6c607c9edd1b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/12/2019
ms.locfileid: "59604653"
---
# <a name="contributing-to-windows-mixed-reality-developer-documentation"></a><span data-ttu-id="c5460-103">Дополнение к документации разработчика Windows Mixed Reality</span><span class="sxs-lookup"><span data-stu-id="c5460-103">Contributing to Windows Mixed Reality developer documentation</span></span>

<span data-ttu-id="c5460-104">Добро пожаловать в [общедоступный репозиторий для документации разработчика Windows Mixed Reality](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span><span class="sxs-lookup"><span data-stu-id="c5460-104">Welcome to the [public repo for Windows Mixed Reality developer documentation](https://github.com/MicrosoftDocs/mixed-reality/tree/master/mixed-reality-docs)!</span></span> <span data-ttu-id="c5460-105">Все статьи, можно создавать и изменять в этом репозитории **будет доступно для просмотра.**</span><span class="sxs-lookup"><span data-stu-id="c5460-105">Any articles you create or edit in this repo **will be visible to the public.**</span></span> 

<span data-ttu-id="c5460-106">Документы по Windows Mixed Reality теперь представлены на платформе docs.microsoft.com, которая использует GitHub flavored Markdown (с помощью функций Markdig).</span><span class="sxs-lookup"><span data-stu-id="c5460-106">Windows Mixed Reality docs are now on the docs.microsoft.com platform, which uses GitHub-flavored Markdown (with Markdig features).</span></span> <span data-ttu-id="c5460-107">По сути, содержимое, редактировать в этот репозиторий возвращает преобразуются в отформатирован и стилизованные страниц, которые отображаются в https://docs.microsoft.com/windows/mixed-reality.</span><span class="sxs-lookup"><span data-stu-id="c5460-107">Essentially, the content you edit in this repo gets turned into formatted and stylized pages that show up at https://docs.microsoft.com/windows/mixed-reality.</span></span> 

<span data-ttu-id="c5460-108">Эта страница описывает основные шаги и правила участия, а также ссылки на основные сведения о Markdown.</span><span class="sxs-lookup"><span data-stu-id="c5460-108">This page covers the basic steps and guidelines for contributing, as well as links to Markdown basics.</span></span> <span data-ttu-id="c5460-109">Спасибо за Ваш вклад!</span><span class="sxs-lookup"><span data-stu-id="c5460-109">Thank you for your contribution!</span></span>

## <a name="before-you-start"></a><span data-ttu-id="c5460-110">Прежде чем начать</span><span class="sxs-lookup"><span data-stu-id="c5460-110">Before you start</span></span>

<span data-ttu-id="c5460-111">Если вы еще не, вам необходимо будет [создайте учетную запись GitHub](https://github.com/join).</span><span class="sxs-lookup"><span data-stu-id="c5460-111">If you don't already have one, you'll need to [create a GitHub account](https://github.com/join).</span></span>

>[!NOTE]
><span data-ttu-id="c5460-112">Если вы являетесь сотрудником корпорации Майкрософт, свяжите учетную запись GitHub, чтобы ваш псевдоним Майкрософт на [портал с открытым исходным кодом Microsoft](https://repos.opensource.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="c5460-112">If you're a Microsoft employee, link your GitHub account to your Microsoft alias on the [Microsoft Open Source portal](https://repos.opensource.microsoft.com/).</span></span> <span data-ttu-id="c5460-113">Присоединяйтесь к **«Microsoft»** и **«MicrosoftDocs»** организаций).</span><span class="sxs-lookup"><span data-stu-id="c5460-113">Join the **"Microsoft"** and **"MicrosoftDocs"** organizations).</span></span>

<span data-ttu-id="c5460-114">При настройке учетной записи GitHub, мы также рекомендуем эти меры безопасности:</span><span class="sxs-lookup"><span data-stu-id="c5460-114">When setting up your GitHub account, we also recommend these security precautions:</span></span>
- <span data-ttu-id="c5460-115">Создание [надежный пароль для учетной записи Github](https://github.com/settings/admin).</span><span class="sxs-lookup"><span data-stu-id="c5460-115">Create a [strong password for your Github account](https://github.com/settings/admin).</span></span>
- <span data-ttu-id="c5460-116">Включить [двухфакторной проверки подлинности](https://github.com/settings/two_factor_authentication/configure).</span><span class="sxs-lookup"><span data-stu-id="c5460-116">Enable [two-factor authentication](https://github.com/settings/two_factor_authentication/configure).</span></span>
- <span data-ttu-id="c5460-117">Сохранить ваши [коды восстановления](https://github.com/settings/auth/recovery-codes) в надежном месте.</span><span class="sxs-lookup"><span data-stu-id="c5460-117">Save your [recovery codes](https://github.com/settings/auth/recovery-codes) in a safe place.</span></span>
- <span data-ttu-id="c5460-118">Обновление вашей [параметры общего профиля](https://github.com/settings/profile).</span><span class="sxs-lookup"><span data-stu-id="c5460-118">Update your [public profile settings](https://github.com/settings/profile).</span></span>
   - <span data-ttu-id="c5460-119">Задайте имя и попробуйте задать вашей *общедоступный почтовый* для *больше не показывать Мой адрес электронной почты*.</span><span class="sxs-lookup"><span data-stu-id="c5460-119">Set your name, and consider setting your *Public email* to *Don't show my email address*.</span></span>
   - <span data-ttu-id="c5460-120">Мы рекомендуем вам добавить фотографию профиля как эскиза будет отображаться на страницах проекта docs, к которым вы внести свой вклад.</span><span class="sxs-lookup"><span data-stu-id="c5460-120">We recommend you upload a profile picture, as a thumbnail will be shown on docs pages to which you contribute.</span></span>
- <span data-ttu-id="c5460-121">Если вы планируете использовать рабочий процесс командной строки, рекомендуется настроить [Git Credential Manager для Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) , не нужно вводить пароль каждый раз внести свой вклад.</span><span class="sxs-lookup"><span data-stu-id="c5460-121">If you plan to use a command line workflow, consider setting up [Git Credential Manager for Windows](https://github.com/Microsoft/Git-Credential-Manager-for-Windows/releases/latest) so that you don't have to enter your password each time you make a contribution.</span></span>

<span data-ttu-id="c5460-122">Эти действия важно, как публикации системы привязывается к GitHub и отобразится как автор или участник для каждой статьи, используя свой псевдоним GitHub.</span><span class="sxs-lookup"><span data-stu-id="c5460-122">Taking these steps is important, as the publishing system is tied to GitHub and you'll be listed as either author or contributor to each article using your GitHub alias.</span></span>

## <a name="editing-an-existing-article"></a><span data-ttu-id="c5460-123">Изменение существующей статьи</span><span class="sxs-lookup"><span data-stu-id="c5460-123">Editing an existing article</span></span>

<span data-ttu-id="c5460-124">Используйте следующий рабочий процесс для обновления *существующей статьи* на сайте GitHub в веб-браузере:</span><span class="sxs-lookup"><span data-stu-id="c5460-124">Use the following workflow to make updates to *an existing article* via GitHub in a web browser:</span></span>

1. <span data-ttu-id="c5460-125">Перейдите к статье, которую вы хотите изменить в папке «смешанный реальности документы».</span><span class="sxs-lookup"><span data-stu-id="c5460-125">Navigate to the article you wish to edit in the "mixed-reality-docs" folder.</span></span>
2. <span data-ttu-id="c5460-126">Нажмите кнопку редактирования (значок карандаша) в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="c5460-126">Select the edit button (pencil icon) in the top right.</span></span> <span data-ttu-id="c5460-127">Это автоматически будет ответвлять высвобождаемые ветви «master» ветви.</span><span class="sxs-lookup"><span data-stu-id="c5460-127">This will automatically fork a disposable branch off the 'master' branch.</span></span>

   ![Изменение статьи.](images/editpage.png)
3. <span data-ttu-id="c5460-129">Изменить содержимое статьи (см. в разделе [«Основные сведения о Markdown»](#markdown-basics) ниже рекомендации).</span><span class="sxs-lookup"><span data-stu-id="c5460-129">Edit the content of the article (see ["Markdown basics"](#markdown-basics) below for guidance).</span></span>
4. <span data-ttu-id="c5460-130">Обновите метаданные в виде соответствующих в верхней части каждой статьи:</span><span class="sxs-lookup"><span data-stu-id="c5460-130">Update metadata as relevant at the top of each article:</span></span>
   * <span data-ttu-id="c5460-131">Заголовок: Это заголовок страницы, который отображается на вкладке браузера при просмотре статьи.</span><span class="sxs-lookup"><span data-stu-id="c5460-131">title: This is the page title that appears in the browser tab when the article is being viewed.</span></span> <span data-ttu-id="c5460-132">Так как это используется для оптимизации поисковой системы и индексирования, не следует изменять заголовок, если не требуется (хотя это не столь важно, перед отправкой общедоступной документации).</span><span class="sxs-lookup"><span data-stu-id="c5460-132">As this is used for SEO and indexing, you shouldn't change the title unless necessary (though this is less critical before documentation goes public).</span></span>
   * <span data-ttu-id="c5460-133">description: Записать краткое описание содержимое статьи.</span><span class="sxs-lookup"><span data-stu-id="c5460-133">description: Write a brief description of the article's content.</span></span> <span data-ttu-id="c5460-134">Это также помогает при оптимизации поисковой системы и обнаружения.</span><span class="sxs-lookup"><span data-stu-id="c5460-134">This aids in SEO and discovery.</span></span>
   * <span data-ttu-id="c5460-135">Автор: Если вы являетесь владельцем основной части страницы, добавьте здесь свой псевдоним GitHub.</span><span class="sxs-lookup"><span data-stu-id="c5460-135">author: If you are the primary owner of the page, add your GitHub alias here.</span></span>
   * <span data-ttu-id="c5460-136">ms.author: Если вы являетесь владельцем основной части страницы, добавьте Microsoft здесь псевдоним (не требуется @microsoft.com, просто псевдоним).</span><span class="sxs-lookup"><span data-stu-id="c5460-136">ms.author: If you are the primary owner of the page, add your Microsoft alias here (you don't need @microsoft.com, just the alias).</span></span>
   * <span data-ttu-id="c5460-137">ms.date: Обновляет дату, при добавлении основных содержимого на страницу, но не для исправления, например пояснение, форматирование, Грамматика, или проверки орфографии.</span><span class="sxs-lookup"><span data-stu-id="c5460-137">ms.date: Update the date if you're adding major content to the page, but not for fixes like clarification, formatting, grammar, or spelling.</span></span>
   * <span data-ttu-id="c5460-138">ключевые слова: Ключевые слова помочь в оптимизации поисковой системы (оптимизация для поисковых систем).</span><span class="sxs-lookup"><span data-stu-id="c5460-138">keywords: Keywords aid in SEO (search engine optimization).</span></span> <span data-ttu-id="c5460-139">Добавьте ключевые слова, разделяя их точкой с запятой и пробелом, относящихся к вашу статью (но знаки препинания, после ключевого слова последнего в списке); не нужно добавить глобальные ключевые слова, которые применяются ко всем статьям, как осуществляется в другом месте.</span><span class="sxs-lookup"><span data-stu-id="c5460-139">Add keywords, separated by a comma and a space, that are specific to your article (but no punctuation after the last keyword in your list); you don't need to add global keywords that apply to all articles, as those are managed elsewhere.</span></span> 
5. <span data-ttu-id="c5460-140">После завершения изменения статьи, прокрутите вниз и выберите **предложить изменение файла** кнопки.</span><span class="sxs-lookup"><span data-stu-id="c5460-140">When you've completed your article edits, scroll down and click the **Propose file change** button.</span></span>
6. <span data-ttu-id="c5460-141">На следующей странице щелкните **создать запрос на Вытягивание** выполнить слияние ветви автоматически создается в «master».</span><span class="sxs-lookup"><span data-stu-id="c5460-141">On the next page, click **Create pull request** to merge your automatically-created branch into 'master.'</span></span>
7. <span data-ttu-id="c5460-142">Повторите предыдущие шаги для следующей статьи, которые вы хотите изменить.</span><span class="sxs-lookup"><span data-stu-id="c5460-142">Repeat the steps above for the next article you want to edit.</span></span>

## <a name="creating-a-new-article"></a><span data-ttu-id="c5460-143">Создание новой статьи</span><span class="sxs-lookup"><span data-stu-id="c5460-143">Creating a new article</span></span>

<span data-ttu-id="c5460-144">Используйте следующий рабочий процесс для *создание новых статей* в репозитории документации на сайте GitHub в веб-браузере:</span><span class="sxs-lookup"><span data-stu-id="c5460-144">Use the following workflow to *create new articles* in the documentation repo via GitHub in a web browser:</span></span>

1. <span data-ttu-id="c5460-145">Создайте вилку ветвь, «master» MicrosoftDocs/смешанной реальности (с помощью **вилки** кнопки в правом верхнем углу).</span><span class="sxs-lookup"><span data-stu-id="c5460-145">Create a fork off the MicrosoftDocs/mixed-reality 'master' branch (using the **Fork** button in the top right).</span></span>

   ![Вилка главной ветви.](images/forkbranch.png)
2. <span data-ttu-id="c5460-147">В папке «смешанный реальности документы», щелкните **создать новый файл** кнопки в правом верхнем углу.</span><span class="sxs-lookup"><span data-stu-id="c5460-147">In the "mixed-reality-docs" folder, click the **Create new file** button in the top right.</span></span>
3. <span data-ttu-id="c5460-148">Создайте имя страницы для статьи (использовать дефисами вместо пробелов и не используйте знаки препинания или апострофы) и добавьте «.md»</span><span class="sxs-lookup"><span data-stu-id="c5460-148">Create a page name for the article (use hyphens instead of spaces and don't use punctuation or apostrophes) and append ".md"</span></span>

   ![Присвойте имя новой страницы.](images/newpagetitle.PNG)
   
   >[!IMPORTANT]
   ><span data-ttu-id="c5460-150">Убедитесь, что вы создаете новую статью из в папке «смешанный, реальность документы».</span><span class="sxs-lookup"><span data-stu-id="c5460-150">Make sure you create the new article from within the "mixed-reality-docs" folder.</span></span> <span data-ttu-id="c5460-151">Это можно проверить путем проверки «/ смешанного реальности docs /» в строке имя нового файла.</span><span class="sxs-lookup"><span data-stu-id="c5460-151">You can confirm this by checking for "/mixed-reality-docs/" in the new file name line.</span></span>

4. <span data-ttu-id="c5460-152">В верхней части новой страницы добавьте следующий блок метаданных:</span><span class="sxs-lookup"><span data-stu-id="c5460-152">At the top of your new page, add the following metadata block:</span></span>

   ```md
   ---
   title:
   description:
   author:
   ms.author:
   ms.date:
   ms.topic: article
   keywords:
   ---
   ```

5. <span data-ttu-id="c5460-153">Заполните поля соответствующими метаданными, следуя инструкциям в [выше разделе](#editing-an-existing-article).</span><span class="sxs-lookup"><span data-stu-id="c5460-153">Fill in the relevant metadata fields per the instructions in the [section above](#editing-an-existing-article).</span></span>
6. <span data-ttu-id="c5460-154">Записи статьи содержимого с помощью [основные сведения о Markdown](#markdown-basics).</span><span class="sxs-lookup"><span data-stu-id="c5460-154">Write article content using [Markdown basics](#markdown-basics).</span></span>
7. <span data-ttu-id="c5460-155">Добавить `## See also` раздел находится в нижней части статьи со ссылками на другие соответствующие статьи.</span><span class="sxs-lookup"><span data-stu-id="c5460-155">Add a `## See also` section at the bottom of the article with links to other relevant articles.</span></span>
8. <span data-ttu-id="c5460-156">Закончив, нажмите кнопку **фиксации нового файла**.</span><span class="sxs-lookup"><span data-stu-id="c5460-156">When finished, click **Commit new file**.</span></span>
9. <span data-ttu-id="c5460-157">Нажмите кнопку **новый запрос на Вытягивание** и слияние ветви «master» вилки в MicrosoftDocs/смешанной реальности «master» (Убедитесь, что стрелка указывает правильный способ использования).</span><span class="sxs-lookup"><span data-stu-id="c5460-157">Click **New pull request** and merge your fork's 'master' branch into MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Создание запроса на Вытягивание из вилки в MicrosoftDocs/смешанной реальности](images/pr_to_master.PNG)

## <a name="markdown-basics"></a><span data-ttu-id="c5460-159">Основные сведения о markdown</span><span class="sxs-lookup"><span data-stu-id="c5460-159">Markdown basics</span></span>

<span data-ttu-id="c5460-160">Следующие ресурсы помогут вам получить изменение документации, с помощью языка разметки Markdown:</span><span class="sxs-lookup"><span data-stu-id="c5460-160">The following resources will help you learn how to edit documentation using the Markdown language:</span></span>

- [<span data-ttu-id="c5460-161">Основные сведения о markdown</span><span class="sxs-lookup"><span data-stu-id="c5460-161">Markdown basics</span></span>](https://help.github.com/articles/basic-writing-and-formatting-syntax/)
- [<span data-ttu-id="c5460-162">Markdown в быстро справочное руководство</span><span class="sxs-lookup"><span data-stu-id="c5460-162">Markdown-at-a-glance reference poster</span></span>](images/MarkdownPoster.pdf)
- [<span data-ttu-id="c5460-163">Дополнительные ресурсы для написания Markdown для docs.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="c5460-163">Additional resources for writing Markdown for docs.microsoft.com</span></span>](https://docs.microsoft.com/contribute/how-to-write-use-markdown)

### <a name="adding-tables"></a><span data-ttu-id="c5460-164">Добавление таблиц</span><span class="sxs-lookup"><span data-stu-id="c5460-164">Adding tables</span></span>

<span data-ttu-id="c5460-165">Из-за как таблицах стилей на сайте docs.microsoft.com они не имеют границы или пользовательские стили, даже если вы попытаетесь встроенных таблиц CSS.</span><span class="sxs-lookup"><span data-stu-id="c5460-165">Because of the way docs.microsoft.com styles tables, they won’t have borders or custom styles, even if you try inline CSS.</span></span> <span data-ttu-id="c5460-166">Он будет работать на короткое время, но в конечном итоге платформы будут удалены из таблицы стилей.</span><span class="sxs-lookup"><span data-stu-id="c5460-166">It will appear to work for a short period of time, but eventually the platform will strip the styling out of the table.</span></span> <span data-ttu-id="c5460-167">Поэтому Подготовьтесь заранее и усложнять таблиц.</span><span class="sxs-lookup"><span data-stu-id="c5460-167">So plan ahead and keep your tables simple.</span></span> <span data-ttu-id="c5460-168">[Здесь — это сайт, упрощает таблиц Markdown](http://www.tablesgenerator.com/markdown_tables).</span><span class="sxs-lookup"><span data-stu-id="c5460-168">[Here’s a site that makes Markdown tables easy](http://www.tablesgenerator.com/markdown_tables).</span></span>

<span data-ttu-id="c5460-169">[Расширении Docs Markdown для Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) также делает таблица создания простой, если вы используете [Visual Studio Code (см. ниже)](#using-visual-studio-code) внесение изменений в документации.</span><span class="sxs-lookup"><span data-stu-id="c5460-169">The [Docs Markdown Extension for Visual Studio Code](https://docs.microsoft.com/teamblog/docs-extension) also makes table generation easy if you're using [Visual Studio Code (see below)](#using-visual-studio-code) to edit the documentation.</span></span>

### <a name="adding-images"></a><span data-ttu-id="c5460-170">Добавление изображений</span><span class="sxs-lookup"><span data-stu-id="c5460-170">Adding images</span></span>

<span data-ttu-id="c5460-171">Вам потребуется передать свои образы в смешанном реальности документы или папки «images» в репозитории, и затем ссылаться на них соответствующим образом в этой статье.</span><span class="sxs-lookup"><span data-stu-id="c5460-171">You’ll need to upload your images to the "mixed-reality-docs/images" folder in the repo, and then reference them appropriately in the article.</span></span> <span data-ttu-id="c5460-172">Образы будут автоматически отображаться в полном размере, означающее, если изображение имеет большой размер, будет заполнено всю ширину элемента статьи.</span><span class="sxs-lookup"><span data-stu-id="c5460-172">Images will automatically show up at full-size, which means if your image is large, it’ll fill the entire width of the article.</span></span> <span data-ttu-id="c5460-173">Таким образом рекомендуется предварительно изменения размера изображения перед их отправкой.</span><span class="sxs-lookup"><span data-stu-id="c5460-173">Thus, we recommend pre-sizing your images before uploading them.</span></span> <span data-ttu-id="c5460-174">Рекомендуемую ширину — в диапазоне от 600 до 700 точек, то, что следует размер вверх или вниз, если это плотных снимок экрана или небольшую часть снимка экрана, соответственно.</span><span class="sxs-lookup"><span data-stu-id="c5460-174">The recommended width is between 600 and 700 pixels, though you should size up or down if it’s a dense screenshot or a fraction of a screenshot, respectively.</span></span>

>[!IMPORTANT]
><span data-ttu-id="c5460-175">Образы можно передать только в разветвление репозитория перед слиянием.</span><span class="sxs-lookup"><span data-stu-id="c5460-175">You can only upload images to your forked repo before merging.</span></span> <span data-ttu-id="c5460-176">Таким образом, если планируется добавление изображений в статью, вам необходимо будет [использование Visual Studio Code](#using-visual-studio-code) сначала Добавление изображений в папку «изображения» в вилку или убедитесь, что вы выполнили следующие действия в веб-браузере:</span><span class="sxs-lookup"><span data-stu-id="c5460-176">So, if you plan on adding images to an article, you'll need to [use Visual Studio Code](#using-visual-studio-code) to add the images to your fork's "images" folder first or make sure you've done the following in a web browser:</span></span>
>
>1. <span data-ttu-id="c5460-177">Создании разветвления в репозиторий MicrosoftDocs/смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="c5460-177">Forked the MicrosoftDocs/mixed-reality repo.</span></span>
>2. <span data-ttu-id="c5460-178">Редактировать статьи в вилке.</span><span class="sxs-lookup"><span data-stu-id="c5460-178">Edited the article in your fork.</span></span>
>3. <span data-ttu-id="c5460-179">Переданных изображений, который вы ссылаетесь в своей статье в папку «смешанный реальность документы и изображения» в вилке.</span><span class="sxs-lookup"><span data-stu-id="c5460-179">Uploaded the images you're referencing in your article to the "mixed-reality-docs/images" folder in your fork.</span></span>
>4. <span data-ttu-id="c5460-180">Создан **запрос на Вытягивание** для слияния вилке ветвью «master» MicrosoftDocs/смешанной реальности.</span><span class="sxs-lookup"><span data-stu-id="c5460-180">Created a **pull request** to merge your fork into the MicrosoftDocs/mixed-reality 'master' branch.</span></span>
>
><span data-ttu-id="c5460-181">Чтобы узнать, как настроить разветвления репозитория, следуйте инструкциям для [создания новой статьи](#creating-a-new-article).</span><span class="sxs-lookup"><span data-stu-id="c5460-181">To learn how to set up your own forked repo, follow the instructions for [creating a new article](#creating-a-new-article).</span></span>

## <a name="previewing-your-work"></a><span data-ttu-id="c5460-182">Предварительный просмотр рабочей</span><span class="sxs-lookup"><span data-stu-id="c5460-182">Previewing your work</span></span>

<span data-ttu-id="c5460-183">Во время редактирования в GitHub с помощью веб-браузер, можно щелкнуть **предварительной версии** вкладки в верхней части страницы, чтобы просмотреть данные перед фиксацией.</span><span class="sxs-lookup"><span data-stu-id="c5460-183">While editing in GitHub via a web browser, you can click the **Preview** tab near the top of the page to preview your work before committing.</span></span> 

>[!NOTE]
><span data-ttu-id="c5460-184">Предварительный просмотр изменений на review.docs.microsoft.com доступен только для сотрудников корпорации Майкрософт</span><span class="sxs-lookup"><span data-stu-id="c5460-184">Previewing your changes on review.docs.microsoft.com is only available to Microsoft employees</span></span>

<span data-ttu-id="c5460-185">Сотрудники корпорации Майкрософт: как только Ваш вклад были объединены в ветви «master», можно увидеть, как будет выглядеть документации перед отправкой его в открытый https://review.docs.microsoft.com/windows/mixed-reality?branch=master (найти статью с помощью оглавление в левом столбце).</span><span class="sxs-lookup"><span data-stu-id="c5460-185">Microsoft employees: once your contributions have been merged into the 'master' branch, you can see what the documentation will look like before it goes public at https://review.docs.microsoft.com/windows/mixed-reality?branch=master (find your article using the table of contents in the left column).</span></span>

## <a name="editing-in-the-browser-vs-editing-with-a-desktop-client"></a><span data-ttu-id="c5460-186">Редактирование в браузере и редактирование с помощью настольного клиента</span><span class="sxs-lookup"><span data-stu-id="c5460-186">Editing in the browser vs. editing with a desktop client</span></span>

<span data-ttu-id="c5460-187">Редактирование в браузере является самым простым способом для быстрого изменения, однако есть несколько недостатков:</span><span class="sxs-lookup"><span data-stu-id="c5460-187">Editing in the browser is the easiest way to make quick changes, however, there are a few disadvantages:</span></span>

- <span data-ttu-id="c5460-188">Вы не получаете проверки орфографии.</span><span class="sxs-lookup"><span data-stu-id="c5460-188">You don't get spell-check.</span></span>
- <span data-ttu-id="c5460-189">Полученный любой смарт связывание с другими статьями (необходимо вручную ввести имя файла из статьи).</span><span class="sxs-lookup"><span data-stu-id="c5460-189">You don't get any smart-linking to other articles (you have to manually type the article's filename).</span></span>
- <span data-ttu-id="c5460-190">Это может быть хлопот для отправки и ссылок на изображения.</span><span class="sxs-lookup"><span data-stu-id="c5460-190">It can be a hassle to upload and reference images.</span></span>

<span data-ttu-id="c5460-191">Если вы бы не иметь появляющихся подобных проблем, вам может потребоваться рабочего стола клиента, например [Visual Studio Code](https://code.visualstudio.com/) пару [полезные расширения](#useful-extensions) для участия в разработке документации.</span><span class="sxs-lookup"><span data-stu-id="c5460-191">If you'd rather not deal with these issues, you may prefer to use a desktop client like [Visual Studio Code](https://code.visualstudio.com/) with a couple [helpful extensions](#useful-extensions) to contribute to documentation.</span></span>

## <a name="using-visual-studio-code"></a><span data-ttu-id="c5460-192">С помощью Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="c5460-192">Using Visual Studio Code</span></span>

<span data-ttu-id="c5460-193">По причинам, в списке [выше](#editing-in-the-browser-vs-editing-with-a-desktop-client), вы можете предпочесть, изменяя с помощью настольного клиента документации вместо веб-браузер.</span><span class="sxs-lookup"><span data-stu-id="c5460-193">For the reasons listed [above](#editing-in-the-browser-vs-editing-with-a-desktop-client), you may prefer using a desktop client to edit documentation instead of a web browser.</span></span> <span data-ttu-id="c5460-194">Мы рекомендуем использовать [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="c5460-194">We recommend using [Visual Studio Code](https://code.visualstudio.com/).</span></span>

### <a name="setup"></a><span data-ttu-id="c5460-195">Установка</span><span class="sxs-lookup"><span data-stu-id="c5460-195">Setup</span></span>

<span data-ttu-id="c5460-196">Выполните следующие действия, чтобы настроить Visual Studio Code для работы с этим репозиторием.</span><span class="sxs-lookup"><span data-stu-id="c5460-196">Follow these steps to configure Visual Studio Code to work with this repo:</span></span>

1. <span data-ttu-id="c5460-197">В веб-браузере:</span><span class="sxs-lookup"><span data-stu-id="c5460-197">In a web browser:</span></span>
    1. <span data-ttu-id="c5460-198">Установка [Git для ПК](https://git-scm.com/downloads).</span><span class="sxs-lookup"><span data-stu-id="c5460-198">Install [Git for your PC](https://git-scm.com/downloads).</span></span>
    2. <span data-ttu-id="c5460-199">Установка [Visual Studio Code](https://code.visualstudio.com/).</span><span class="sxs-lookup"><span data-stu-id="c5460-199">Install [Visual Studio Code](https://code.visualstudio.com/).</span></span>
    3. <span data-ttu-id="c5460-200">[Разветвление MicrosoftDocs/смешанной реальности](#creating-a-new-article) Если у вас еще нет.</span><span class="sxs-lookup"><span data-stu-id="c5460-200">[Fork MicrosoftDocs/mixed-reality](#creating-a-new-article) if you haven't already.</span></span>
    4. <span data-ttu-id="c5460-201">В этой вилке щелкните **клонировать или скачать** и скопируйте URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="c5460-201">In your fork, click **Clone or download** and copy the URL.</span></span>
2. <span data-ttu-id="c5460-202">Создайте локальный клон разветвления в Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="c5460-202">Create a local clone of your fork in Visual Studio Code:</span></span>
    1. <span data-ttu-id="c5460-203">Из **представление** меню, выберите **палитру команд**.</span><span class="sxs-lookup"><span data-stu-id="c5460-203">From the **View** menu, select **Command Palette**.</span></span>
    2. <span data-ttu-id="c5460-204">Тип «Git:Clone.»</span><span class="sxs-lookup"><span data-stu-id="c5460-204">Type "Git:Clone."</span></span>
    3. <span data-ttu-id="c5460-205">Вставьте скопированный URL-адрес.</span><span class="sxs-lookup"><span data-stu-id="c5460-205">Paste the URL you just copied.</span></span>
    4. <span data-ttu-id="c5460-206">Укажите место для сохранения копии на вашем Компьютере.</span><span class="sxs-lookup"><span data-stu-id="c5460-206">Choose where to save the clone on your PC.</span></span>
    5. <span data-ttu-id="c5460-207">Нажмите кнопку **откройте репозиторий** во всплывающем окне.</span><span class="sxs-lookup"><span data-stu-id="c5460-207">Click **Open repo** in the pop-up.</span></span>

### <a name="editing-documentation"></a><span data-ttu-id="c5460-208">Редактирование документации</span><span class="sxs-lookup"><span data-stu-id="c5460-208">Editing documentation</span></span>

<span data-ttu-id="c5460-209">Используйте следующий рабочий процесс для внесения изменений в документации с помощью Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="c5460-209">Use the following workflow to make changes to the documentation with Visual Studio Code:</span></span>

>[!NOTE]
><span data-ttu-id="c5460-210">Все рекомендации для [редактирование](#editing-an-existing-article) и [создание](#creating-a-new-article) статей и [основы редактирования разметки Markdown](#markdown-basics), выше применяется при использовании Visual Studio Code, а также.</span><span class="sxs-lookup"><span data-stu-id="c5460-210">All the guidance for [editing](#editing-an-existing-article) and [creating](#creating-a-new-article) articles, and the [basics of editing Markdown](#markdown-basics), from above applies when using Visual Studio Code as well.</span></span>

1. <span data-ttu-id="c5460-211">Убедитесь, что клонированный вилки в официальный репозиторий.</span><span class="sxs-lookup"><span data-stu-id="c5460-211">Make sure your cloned fork is up-to-date with the official repo.</span></span>
   1. <span data-ttu-id="c5460-212">В веб-браузер, создайте запрос на Вытягивание, чтобы синхронизировать последние изменения других участников в MicrosoftDocs/смешанной реальности «master», в свою вилку (Убедитесь, что стрелка указывает правильный способ).</span><span class="sxs-lookup"><span data-stu-id="c5460-212">In a web browser, create a pull request to sync recent changes from other contributors in MicrosoftDocs/mixed-reality 'master' to your fork (make sure the arrow is pointing the right way).</span></span>
      
      ![Синхронизировать изменения из MicrosoftDocs/смешанной реальности вилке](images/sync_repos.PNG)
   2. <span data-ttu-id="c5460-214">В Visual Studio Code нажмите кнопку синхронизации для синхронизации только что обновленный вилки к локальному клону.</span><span class="sxs-lookup"><span data-stu-id="c5460-214">In Visual Studio Code, click the sync button to sync your freshly updated fork to the local clone.</span></span>
      
      ![Нажмите кнопку "Синхронизация"](images/sync_clone.png)
2. <span data-ttu-id="c5460-216">Создание или изменение статьи в клонированном репозитории с помощью Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c5460-216">Create or edit articles in your cloned repo using Visual Studio Code.</span></span>
   1. <span data-ttu-id="c5460-217">Измените одну или несколько статей (Добавить папку «изображения» образов, при необходимости).</span><span class="sxs-lookup"><span data-stu-id="c5460-217">Edit one or more articles (add images to “images” folder if necessary).</span></span>
   2. <span data-ttu-id="c5460-218">**Сохранить** изменения в **Explorer**.</span><span class="sxs-lookup"><span data-stu-id="c5460-218">**Save** changes in **Explorer**.</span></span>
      
      ![Выберите «Сохранить все» в обозревателе](images/explorer_save.png)
   3. <span data-ttu-id="c5460-220">**Фиксация всех изменений** изменения в **системы управления версиями** (записи сообщения фиксации при появлении запроса).</span><span class="sxs-lookup"><span data-stu-id="c5460-220">**Commit all** changes in **Source Control** (write commit message when prompted).</span></span>
      
      ![Выберите «Сохранить все» в системе управления версиями](images/source_control_commit.png)
   4. <span data-ttu-id="c5460-222">Нажмите кнопку **синхронизации** кнопку, чтобы синхронизация внесенных изменений обратно в исходный репозиторий (разветвление на GitHub).</span><span class="sxs-lookup"><span data-stu-id="c5460-222">Click the **sync** button to sync your changes back to origin (your fork on GitHub).</span></span>
      
      ![Нажмите кнопку "Синхронизация"](images/sync_back.png)
3. <span data-ttu-id="c5460-224">В веб-браузер, создайте запрос на Вытягивание, чтобы синхронизировать изменения в вилке к MicrosoftDocs/смешанной реальности «master» (Убедитесь, что стрелка указывает правильный способ использования).</span><span class="sxs-lookup"><span data-stu-id="c5460-224">In a web browser, create a pull request to sync new changes in your fork back to MicrosoftDocs/mixed-reality 'master' (make sure the arrow is pointing the correct way).</span></span>

   ![Создание запроса на Вытягивание из вилки в MicrosoftDocs/смешанной реальности](images/pr_to_master.PNG)

### <a name="useful-extensions"></a><span data-ttu-id="c5460-226">Полезные расширения</span><span class="sxs-lookup"><span data-stu-id="c5460-226">Useful extensions</span></span>

<span data-ttu-id="c5460-227">Следующие расширения Visual Studio Code очень полезны при редактировании документации:</span><span class="sxs-lookup"><span data-stu-id="c5460-227">The following Visual Studio Code extensions are very useful when editing documentation:</span></span>

- <span data-ttu-id="c5460-228">[Расширения docs Markdown для Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) -использование **Alt + M** откроется меню создания параметрами, такими как документации:</span><span class="sxs-lookup"><span data-stu-id="c5460-228">[Docs Markdown Extension for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=docsmsft.docs-authoring-pack) - Use **Alt+M** to bring up a menu of docs authoring options like:</span></span>
   - <span data-ttu-id="c5460-229">Справочник по и поиска образов, отправленные вами.</span><span class="sxs-lookup"><span data-stu-id="c5460-229">Search and reference images you've uploaded.</span></span>
   - <span data-ttu-id="c5460-230">Добавление форматирования, такие как списки, таблицы, и вызовами документации Майкрософт, например `>[!NOTE]`.</span><span class="sxs-lookup"><span data-stu-id="c5460-230">Add formatting like lists, tables, and docs-specific call-outs like `>[!NOTE]`.</span></span>
   - <span data-ttu-id="c5460-231">Поиск и ссылки на внутренние ссылки и закладки (ссылки на разделы на странице).</span><span class="sxs-lookup"><span data-stu-id="c5460-231">Search and reference internal links and bookmarks (links to specific sections within a page).</span></span>
   - <span data-ttu-id="c5460-232">Ошибки форматирования будут выделены (наведите указатель мыши ошибки Дополнительные сведения).</span><span class="sxs-lookup"><span data-stu-id="c5460-232">Formatting errors are highlighted (hover your mouse over the error to learn more).</span></span>
- <span data-ttu-id="c5460-233">[Код проверки орфографии](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) -слов с ошибками будут подчеркнуты; щелкните правой кнопкой мыши на неправильно написанное слово можно изменить или сохранить его в словарь.</span><span class="sxs-lookup"><span data-stu-id="c5460-233">[Code Spell Checker](https://marketplace.visualstudio.com/items?itemName=streetsidesoftware.code-spell-checker) - misspelled words will be underlined; right-click on a misspelled word to change it or save it to the dictionary.</span></span>
