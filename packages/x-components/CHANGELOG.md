# Change Log

All notable changes to this project will be documented in this file.
See [Conventional Commits](https://conventionalcommits.org) for commit guidelines.

## 6.0.0-alpha.1 (2024-09-04)


### ⚠ BREAKING CHANGES

* version 6 of x-components is only compatible with vue 3
* refactors the GlobalXBus to use a prop to receive the listeners instead of relying on attributes.
* **simple-filter:** use cssClasses prop to pass classes through the component in Vue 3 instead of class or :class when using RenderlessFilter or SimpleFilter components
* **use-register-x-module:** get rid of useRegisterXModule composable. Use XPlugin.registerXModule(xModule) or InstallXOptions.initialXModules instead
* **scroll:** `WindowScroll' component will no longer be available and has been removed.
* `MainScroll` drops the usage of `NoElement` as root element and uses a div instead. This extra div could break the style of an application that relies on `MainScroll` rendering their content directly.
`MainScrollItem` drops the usage of `NoElement` if no `tag` prop is passed and uses a div as fallback.
* **ColumnPickerMixin:** `BaseColumnPickerDropdown` component will no longer emit the `change` event, use `update:modelValue` instead. 
`BaseColumnPickerDropdown` prop for the selected columns was renamed from `value` to `modelValue`.

`BaseColumnPickerList` component will no longer emit the `change` event, use `update:modelValue` instead. 
`BaseColumnPickerList` prop for the selected columns was renamed from `value` to `modelValue`.

`ColumnPickerMixin` has been removed.
* **sort-mixin:** base-dropdown component will no longer emit the `change` event, use `update:modelValue` instead. 
base-dropdown prop for the selected item was renamed from `value` to `modelValue`.
* **components:** remove deprecated origins from (#1344)
* **facets:** The '__unknown-facet__' value for a facetId is deprecated: it has been replaced by the UNKNOWN_FACET_KEY constant, whose value is '__unknown__'.

Co-authored-by: Guillermo Cacheda <cachedacodes@gmail.com>
* setPageSize search module mutation has been replaced by the setConfig mutation. 
setTaggingConfig tagging module mutation and setFacetsConfig facets module mutation have been replaced by the mergeConfig mutation.

EMP-2328
* the property 'querySuggestions' in '' now returns the query suggestions that should be displayed based on the module's config. A new property called 'fullQuerySuggestions' returns all the query suggestions in the module

EMP-1463
* **deps:** minimum node version required is 18.
* **deps:** minimum version required is node v18

EMP-274
* **design-system:** The `x-components` design system has been deprecated. 
The exported theme is no longer available. If you need support for the old design system you should import `@empathyco/x-components/design-system/deprecated-full-theme.css`.
* **design-system:** `x-grid-list` and `x-grid-list__item` classes have been removed from `BaseGrid` component.
* **design-system:** `x-grid-list--cols-{columns}` has been renamed to `x-base-grid--cols-{columns}`
* **design-system:** `x-list` class has been removed from the following components: 

   `BaseModal`, `BaseSuggetions`, `BaseTabsPanel`, `Facets`, `FiltersList`, `FiltersSearch`, `IdentifierResults`, `MyHistory`, `PartialResultList`, `ResultVariantSelector`, `Recommendations`, `RelatedTags`, `SlidingPanel`, `SelectedFiltersList`.
   
* **design-system:** `FixedHeaderAndAsidesLayout` `MultiColumnMaxWidthLayout` and `SingleColumnLayout` have been deprecated.
* **design-system:** `BaseModal` default opacity has changed from `0.7` to `0.3`.
* **design-system:** `x-list__item` class has been removed from `BaseTabsPanel` component.
* **design-system:** `x-message` class has been removed from `Redirection` component.

EMP-133

Co-authored-by: Diego Pascual <diegopf@users.noreply.github.com>
Co-authored-by: Manuel Navarro <manueln@empathy.co>
* **design-system:** Old `design-system` `progress-bar` styles are now located in the `deprecated-full-theme.css` file.
* **design-system:** Renamed `x-progress-bar__line` class to `x-progress-bar-fill`.
* `base-column-picker-list` structure changes. It now wraps the buttons in a div instead of using ul and li. Additionally, the class for the selected option has been changed to `x-selected`.
* **design-system:** Old `design-system` `Tag` styles are now located in the  `deprecated-full-theme.css` file.
* **design-system:** Old `x-tag--is-curated` and `x-tag--is-selected` classes are no longer used by `RelatedTag` component. 
* **design-system:** design system scroll styles are deprecated. To continue using them import from deprecated-full-theme.css
* **design-system:** Old design-system `Icon` styles are now located in the `deprecated-full-theme.css` file.
Removed `checkbox-card`, `nq1`, `nq2`, `nq3`, and `nq4 icons`.
* **components:** class `x-picture__image` renamed to `x-picture-image`, deprecate classes `x-picture__image--placeholder` and `x-picture__image--fallback`
* **components:** Renamed `SlidingPanel` css classes `x-sliding-panel--at-start` and `x-sliding-panel--at-end` to `x-sliding-panel-at-start` and `x-sliding-panel-at-end` respectively.
* **components:** Renamed `SlidingPanel` buttons css classes `x-sliding-panel__button-left` and `x-sliding-panel__button-right` to `x-sliding-panel-button-left` and `x-sliding-panel-button-right` respectively.
* **components:** Old design-system `SlidingPanel` styles (including the updated button classes) are now located in the `deprecated-full-theme.css` file.
* **history-queries:** Renamed `removeHistoryQueryClass` prop to `removeButtonClass`.
* Rename `x-grid` class to `x-grid-list`.
* Rename `x-grid__item` class to `x-grid-list__item`.
* Rename `x-grid--cols-{cols}` class to `x-grid-list--cols-{cols}`.
* **design-system:** suggestion and suggestion group styles are now deprecated. To continue using them import from `deprecated-full-theme.css`.
* Rename `NextQueryPreviewMounted` to `NextQueryPreviewMountedHook` and `QueryPreviewRemoved` to `QueryPreviewUnmountedHook`
* **components:** Removes `queryHTML` slot scope prop from `BaseSuggestion`, `PopularSearch` `QuerySuggestion` and `HistoryQuery`. Use the new `Highlight` component instead.
* the event `SearchResponseProvided` was renamed to `SearchResponseChanged`
* **design-system:** the old design system button styles are now located in the `deprecated-full-theme.css`, if a setup is not using the new design system, it must import this file.
* **components:** `facets` are now optional in `Suggestion`.
* **tagging:** `tagging` property of `Taggable` and `queryTagging` property of `SearchResponse` are optional.
* **result:** `Result` model properties are optional, except `id`, `modelName` and `tagging`.
* **facets:** Removed the `setFilter`mutation from `facets` X-Module. Use `mutateFilter` instead.
* **facets:** Modified the `HierarchicalFilter.children` Model type. Now it is an `Array<HierarchicalFilter>` instead of an array of ids.
* `--x-number-aspect-ratio-picture` is now inverted. Previously a value of 2 meant that it was twice taller than wider. Now it means twice wider than taller.
* `XAPI` is now available now at `window.InterfaceX`.
* **facets:** Renamed method `registerFilterModifier` in `FilterEntityFactory` to `registerModifierByFacetId`.
* **facets:** Changed `modifiers` parameter of `registerFilterModifier` in `FilterEntityFactory` from a single array in favour of rest parameters.
* Request types moved to `x-types` package. Change the imports from `x-adapter` to `x-type`.
* Removed `TaggingInfo` type. Use `TaggingRequest` from `@empathyco/x-types` instead.
* **eslint:** Vue config now also extends the recommended config from vuejs-accesibility plugin.
* Remove `selected` and `previous` logic from related tags.
* Remove `EmpathyRequestRelatedTagsQueryMapper`.
* **components:** Removed `CollapseFromTop` Animation. Use `animateScale()` instead.
* **components:** Removed `TranslateFromLeft` and `TranslateFromRight` components. Use `animateTranslate('left')` and `animateTranslate('right')` instead.
* **facets:** Remove `BaseFilter` component. Use `RenderlessFilter`instead.
* **components:** `SlidingPanel` buttons do not have the round variant set by default.
* **components:** ArrowIcon changed to ArrowLeftIcon.
* **storage-service:** `StorageService` has been renamed to `BrowserStorageService`.
* **scroll:** `BaseIdScroll` has been renamed to `Scroll`. It should be imported from `@empathyco/x-components/scroll`
* **scroll:** `BaseMainScroll` has been renamed to `WindowScroll`. It should be imported from `@empathyco/x-components/scroll`
* **scroll:** `BaseScrollToTop` has been renamed to `ScrollToTop`. It should be imported from `@empathyco/x-components/scroll`
* **scroll:** `UserReachedScrollStart` event now emits a boolean indicating the change of this state.
* **scroll:** `UserAlmostReachedScrollEnd` event now emits a boolean indicating the change of this state.
* **scroll:** `UserReachedScrollEnd` event now emits a boolean indicating the change of this state.
* Slots that are created using properties like the `modelName` or the `id` of different objects, now are named using the kebab-case version of those values. This affects the following components: `BaseGrid`, `Facets` and `SelectedFiltersList`. Examples:
`<template #Result="{ ... }">` now is `<template #result="{ ... }">`
`<template #NextQueriesGroup="{ ... }">` now is `<template #next-queries-group="{ ... }">`
`<template #hierarchical_category="{ ... }">` now is `<template #hierarchical-category="{ ... }">`
* **no-suggestions:** Remove `no-suggestions` module
* **design-system:** Rename `Layout` to `MultiColumnMaxWidthLayout`
* **facets:** Rename `Filters` component to `FiltersList`.
* **facets:** Remove `MultiSelectFilters` component. Filters are multi-select by default. Apply the `SingleSelectModifier` using the `FilterEntityFactory` to make the desired `Facet` single select.
* **facets:** Refactor `HierarchicalFilter.children` field. Now, this field is a list of the `Filter.ids` of the children filter. All `HierarchicalFilter`s are flattened in the `Facet.filters` list.
* **facets:** Remove `facets` prop in the `Facets` component to provide `Facets` to the state. Use the `FacetsProvider` component instead.
* **facets:** Remove `UserChangedSelectedFilters` event from `Facets` component. Use `FacetsProvider` component instead.
* **facets:** Remove `UserClickedClearFacetFilters` event. `UserClickedClearAllFilters` is emitted instead. Its payload is now a list of `Facet.id`s.
* **facets:** Rename `UserClickedFacetAllFilter` event to `UserClickedAllFilter`. Its payload is now a list of `Facet.id`s.
* **facets:** Remove `BackendFacetsChanged` event. Use `FacetsChanged` event instead.
* **facets:** Remove `BackendFacetsProvided` event. Use `FacetsGroupProvided` instead.
* **facets:** Remove `FrontendFacetsChanged` event. Use `FacetsGroupProvided` instead.
* **facets:** Remove `FacetMultiSelectChanged` event. `Filter`s are multi-select by default. Apply the `SingleSelectModifier` using the `FilterEntityFactory` to make the desired `Facet` single select.
* **facets:** Change `UserModifiedEditableNumberRangeFilter` payload. Now it is the `EditableNumberRangeFilter` filter with the new range value.
* **components:** Remove `hideIntegerDecimals` from `currency-formatter` util,  `base-currency` component.
* **facets-next:** Rename `EmpathyFilterMapper` to `EmpathyFacetFilterMapper`. Response filter mappers now map the API value in the `id` filters property.  `EmpathyHierarchicalFacetMapper` now flattens and stores all the filters in the `filter` property. `EmpathyHierarchicalFacetMapper` now only maps filters ids in `HierarchicalFilter` children. Bump up `@empathyco/x-types` major version in `@empathyco/x-adapter`.
* **design-system:** Design system styles have now to be imported from `@empathy/x-components/design-system` instead of @empathy/x-components/css`
* **facets:** Base prefix was remove from the following components: `BaseFilters`, `BaseFiltersSearch`, `BaseSlicedFilters`, `BaseAllFilter`, `BaseHierarchicalFilter`, `BaseNumberRangeFilter` and `BaseSimpleFilter`.
* **facets:** Filters which have selected property now extends from BooleanFilter
* **currency-formatter:** remove `CurrencyOptions` from `XConfig` and its default value from `DEFAULT_X_CONFIG`,
remove `ConfigCurrencyChanged` event from `XEventsTypes` and remove `currency` property from `SnippetConfig`.
* **exports:** Rename some wires due to collisions between other exported members (i.e. actions/getters):
`facets` ->  `setFacets` to `setFacetsWire`, `toggleSimpleFilter` to `toggleSimpleFilterWire`, `toggleHierarchicalFilter` to `toggleHierarchicalFilterWire`, `toggleNumberRangerFilter` to `toggleNumberRangerFilterWire`, `clearFacetsSelectedFilters` to `clearFacetsSelectedFiltersWire`, `clearFacetSelectedFilters` to `clearFacetSelectedFiltersWire` and `clearSelectedFilters` to `clearSelectedFiltersWire`.
`history-queries` -> `loadHistoryQueriesFromBrowserStorage` to `loadHistoryQueriesFromBrowserStorageWire`.
`next-queries` -> `fetchAndSaveNextQueries` to `fetchAndSaveNextQueriesWire` and `setQueryFromLastHistoryQuery` to `setQueryFromLastHistoryQueryWire`.
`query-suggestions` -> `fetchAndSaveSuggestions` to `fetchAndSaveSuggestionsWire` and `cancelFetchAndSaveSuggestions` to `cancelFetchAndSaveSuggestionsWire`.
`related-tags` -> `fetchAndSaveRelatedTags` to `fetchAndSaveRelatedTagsWire`, `cancelFetchAndSaveRelatedTags` to `cancelFetchAndSaveRelatedTagsWire` and `toggleRelatedTag` to `toggleRelatedTagWire`.
`search` ->  `fetchAndSaveSearchResponse` to `fetchAndSaveSearchResponseWire` and `cancelFetchAndSaveSearchResponse` to `cancelFetchAndSaveSearchResponseWire`.

Rename exports of `getters` named `request` to `moduleName` + `Request` due to collisions between modules.
Rename `ClearFilters` class to `ClearSelectedFilters`.
* **components:** `BaseModalContainer` has been split into 2 new components: `BaseEventsModal`, which acts like the old component, but with the `eventToEmitOnClose` prop renamed to `bodyClickEvent`. `BaseModal` now acts as a dumb modal that receives its open state via props.
`BaseCloseButton` has been renamed to `BaseEventsCloseButton`
`BaseOpenButton` has been renamed to `BaseEventsOpenButton`
Events have been renamed: `UserOpenedX` -> `UserClickedOpenX`, `UserClosedX` -> `UserClickedCloseX`
* rename actions in several modules: Popular searches `getSuggestions` → `fetchSuggestions`.
Query suggestions: `getAndSaveSuggestions` → `fetchAndSaveSuggestions`,  `getSuggestions` → `fetchSuggestions`.

### Features

* **actions:** generalize request actions ([5aef8ce](https://github.com/empathyco/x/commit/5aef8ced9c5e331f5ddd9c321a26bb66534fb2d8)), closes [EX-2663](https://searchbroker.atlassian.net/browse/EX-2663)
* adapt `base-column-picker-list` to use the XDS component of button group (#1115) ([7057b8f](https://github.com/empathyco/x/commit/7057b8f7cd7f1e20ad248c40e8da97450895cd26)), closes [EX-8144](https://searchbroker.atlassian.net/browse/EX-8144)
* Adapt Result mapping according to new API standard (#1039) ([89186b6](https://github.com/empathyco/x/commit/89186b604d72f18bce257b88b536243c11c5ddf3))
* **adapter:** disable cancel http client (#658) ([3b5b86d](https://github.com/empathyco/x/commit/3b5b86d4725edefa084181a704df716a389eecbc)), closes [EX-6875](https://searchbroker.atlassian.net/browse/EX-6875)
* **adapter:** use the `x-adapter-platform` (#565) ([55bccb4](https://github.com/empathyco/x/commit/55bccb4118bc0fd2468b736eb470942aaae2e4ae)), closes [EX-5936](https://searchbroker.atlassian.net/browse/EX-5936)
* add 'my_history' as feature location (#587) ([7b0263e](https://github.com/empathyco/x/commit/7b0263e23c9afb2af61174ac53bdedd3eb4263ba)), closes [EX-6527](https://searchbroker.atlassian.net/browse/EX-6527)
* add `alt-text` accessibility ([da5a10a](https://github.com/empathyco/x/commit/da5a10a236aae5fae96943fe0ad54849df15e7f5)), closes [EX-5930](https://searchbroker.atlassian.net/browse/EX-5930)
* add `dynamic-props` mixin (#798) ([defafbb](https://github.com/empathyco/x/commit/defafbb2c40f51e3c44474b469b353472a91a828)), closes [EX-7220](https://searchbroker.atlassian.net/browse/EX-7220)
* add `filterItemClass` prop to `HierarchicalFilter` (#1135) ([99de550](https://github.com/empathyco/x/commit/99de5508e64e2d8c5ea849f89a3cc81472527c4d))
* add `Highlight` component (#872) ([1b5aa57](https://github.com/empathyco/x/commit/1b5aa5793b7916ec0433b4110b7ef355f882f4f6)), closes [EX-7468](https://searchbroker.atlassian.net/browse/EX-7468)
* add `prettier-plugin-tailwindcss` (#1033) ([c3eae8b](https://github.com/empathyco/x/commit/c3eae8bef0a75fa1e78f1190947a74fa9269d6bd)), closes [EX-7884](https://searchbroker.atlassian.net/browse/EX-7884)
* add `queriesPreview` option to snippet config (#654) ([7733c98](https://github.com/empathyco/x/commit/7733c9856b2859574ca0cace9c79b8b58545f46a)), closes [EX-6849](https://searchbroker.atlassian.net/browse/EX-6849)
* Add `setSnippetConfig` function to the `X` API ([8c53cc7](https://github.com/empathyco/x/commit/8c53cc74cdd95e1a8ef3aa8167206cd81685d1e7)), closes [EX-5384](https://searchbroker.atlassian.net/browse/EX-5384)
* add `uiLang` parameter (#714) ([f4108d4](https://github.com/empathyco/x/commit/f4108d4a76582dac7b1f8cd240e91f226e7b1ad5)), closes [EX-6855](https://searchbroker.atlassian.net/browse/EX-6855)
* add `vue devtools` plugin to ease `XEvents` and `wiring` visualization (#215) ([bd148ec](https://github.com/empathyco/x/commit/bd148ecb9682f8d4161d278c03f110f8f050d323)), closes [EX-7032](https://searchbroker.atlassian.net/browse/EX-7032)
* add alias for the query suggestions that should be displayed (#1247) ([4de1ccc](https://github.com/empathyco/x/commit/4de1ccc2f287749f91a1014edc3c127c9207bc52))
* Add close event to BaseXAPI (#1091) ([1aaaeb0](https://github.com/empathyco/x/commit/1aaaeb0dd2cb20a90655e9afe7622de67616e708)), closes [EX-8050](https://searchbroker.atlassian.net/browse/EX-8050)
* Add directional origins for translate animations (#773) ([9f4a0b0](https://github.com/empathyco/x/commit/9f4a0b03c675291672081388e42fcec725ab594d))
* add dynamic classes to the suggestion item inside the `base-suggestions` (#1008) ([3e0b683](https://github.com/empathyco/x/commit/3e0b683eb83b9b2e9f6ebb0a17b80a9ff46d6e3c)), closes [EX-7834](https://searchbroker.atlassian.net/browse/EX-7834)
* add dynamic props for title to promoteds and banner (#1168) ([1914f01](https://github.com/empathyco/x/commit/1914f01981a2de48c65d3a88cfcedc26c2a293fe))
* add filters to the query preview request (#1292) ([7f20022](https://github.com/empathyco/x/commit/7f20022eee593460681bfb1c4d574162f325cc05))
* add position on Banner and Promoted models (#800) ([e7393fb](https://github.com/empathyco/x/commit/e7393fbce8d0767d3c762aa714fe94e162203a12)), closes [EX-7293](https://searchbroker.atlassian.net/browse/EX-7293)
* Add search input hover events (#772) ([393cc87](https://github.com/empathyco/x/commit/393cc877457f618396a5b71a7a826e6e8d139c3a)), closes [EX-7177](https://searchbroker.atlassian.net/browse/EX-7177)
* add settings icon (#589) ([7f93849](https://github.com/empathyco/x/commit/7f9384915718805809ff733f2be60ae6ebb01910)), closes [EX-6519](https://searchbroker.atlassian.net/browse/EX-6519)
* add status to every store module ([b876d1d](https://github.com/empathyco/x/commit/b876d1d98454ebcc811222ee89dd5efa4d16c2e3)), closes [EX-2435](https://searchbroker.atlassian.net/browse/EX-2435)
* add sticky filters (#1113) ([3b51b60](https://github.com/empathyco/x/commit/3b51b6045a283f9f27dd7c6e16dec7f68a8a2921)), closes [EX-8076](https://searchbroker.atlassian.net/browse/EX-8076)
* add view to test base-result-link accessibility (#972) ([21d185a](https://github.com/empathyco/x/commit/21d185a8a107f95be4436dabfbeffe83bc7dcd62))
* adding edocs preview ([8580a72](https://github.com/empathyco/x/commit/8580a72fa3b9125ad7a487995eabedb7ecfbde2b))
* **animation:** extract mixin from `CollapseHeight` and `CollapseWidth` animations. ([905aba9](https://github.com/empathyco/x/commit/905aba9baa8e98797db76a8f6f48abe31d07520a)), closes [EX-2827](https://searchbroker.atlassian.net/browse/EX-2827)
* **animations:** add `CollapseWidth` animation ([0523ca4](https://github.com/empathyco/x/commit/0523ca446c83df1a23bf480939e216dc70f9be69)), closes [EX-2826](https://searchbroker.atlassian.net/browse/EX-2826)
* **animations:** add collapse-height component ([5f4cb55](https://github.com/empathyco/x/commit/5f4cb550d555cf16bfd1f6eb8ae48d036f760fd3)), closes [EX-2661](https://searchbroker.atlassian.net/browse/EX-2661)
* **animations:** add new `TranslateFromRight` animation ([e13561f](https://github.com/empathyco/x/commit/e13561f79e6ec04fed9ed99e56d75254f40858f5)), closes [EX-4696](https://searchbroker.atlassian.net/browse/EX-4696)
* **animations:** add staggering-transition-group component ([5df34f5](https://github.com/empathyco/x/commit/5df34f53130044a1d885e12b588a20114a8f03ca)), closes [EX-2208](https://searchbroker.atlassian.net/browse/EX-2208)
* **animations:** added z-index within staggered animations styles ([63a622a](https://github.com/empathyco/x/commit/63a622a5091c85915f4eba5fcdd5b98776d9b3f3)), closes [EX-3082](https://searchbroker.atlassian.net/browse/EX-3082)
* **animations:** fade and slide animation component ([b3c23f0](https://github.com/empathyco/x/commit/b3c23f0e7d7e3f94f34bc9b96e340b5f0c1ff64b)), closes [EX-1867](https://searchbroker.atlassian.net/browse/EX-1867)
* **animations:** fix `FadeAndSlide` and `StaggeredFadeAndSlide` animations ([1e31036](https://github.com/empathyco/x/commit/1e3103627d5d90ac73e2b19bf746429f737d2d8e)), closes [EX-3813](https://searchbroker.atlassian.net/browse/EX-3813)
* **api-extractor:** refactor api-extractor doc generation ([d77d556](https://github.com/empathyco/x/commit/d77d5567d3ba80e2013a7dc3989d3f686872224f)), closes [EX-2152](https://searchbroker.atlassian.net/browse/EX-2152)
* apply dynamic css mixin to sliding panel and column picker list buttons (#815) ([4cc040d](https://github.com/empathyco/x/commit/4cc040d7d7c4751a5f31c6e36acfa64d28cbb23d)), closes [EX-7224](https://searchbroker.atlassian.net/browse/EX-7224)
* **banner:** add support without title and no clickable (#1069) ([7207767](https://github.com/empathyco/x/commit/72077675691dc8fab7361f64e0302aa8d33213fa))
* **base-column-picker-list:** add `base-column-picker-list` component ([239b4b7](https://github.com/empathyco/x/commit/239b4b75b8482cacec32ac27227885a658ed96de)), closes [EX-3295](https://searchbroker.atlassian.net/browse/EX-3295)
* **base-components:** add `base-id-modal`, `base-id-modal-open` and `base-id-moda-close` components ([6a3f53e](https://github.com/empathyco/x/commit/6a3f53ef6838a3ab2e4d93153fdcfac7d6e100de)), closes [EX-3100](https://searchbroker.atlassian.net/browse/EX-3100)
* **base-components:** add base filters component ([caa5129](https://github.com/empathyco/x/commit/caa5129eed13de2f4d38efb3cbffefb5114cdd90)), closes [EX-2513](https://searchbroker.atlassian.net/browse/EX-2513)
* **base-components:** add BaseNumberRangeFilter component ([5a48a70](https://github.com/empathyco/x/commit/5a48a70b529f4eca6d52b3e39047a3a31f59bc73)), closes [EX-2797](https://searchbroker.atlassian.net/browse/EX-2797)
* **base-currency:** componente which renders a formatted value with a format passed both by props ([0d68eac](https://github.com/empathyco/x/commit/0d68eacdcfc188abddece091891791e441389977)), closes [EX-2758](https://searchbroker.atlassian.net/browse/EX-2758)
* **base-filters-search:** add base filters search component ([17848ad](https://github.com/empathyco/x/commit/17848ad65fb657e4a849dd30c9515c98aa6bb0d0)), closes [EX-2234](https://searchbroker.atlassian.net/browse/EX-2234)
* **base-grid:** add base-grid component ([8bc1092](https://github.com/empathyco/x/commit/8bc109239c1e1483ff9b2bf6e2712c01429aad29)), closes [EX-3245](https://searchbroker.atlassian.net/browse/EX-3245)
* **base-header-toggle-panel:** component base-header-toggle-panel which manages base toggle panel ([61dc392](https://github.com/empathyco/x/commit/61dc392a56ca272e9f3ba062b142bf0f4baafbb3)), closes [EX-2232](https://searchbroker.atlassian.net/browse/EX-2232)
* **base-id-modal:** migrate to composition API (#1500) ([6274c67](https://github.com/empathyco/x/commit/6274c676946536c9c1c4e54205ebda18c79b8f55))
* **base-modal-container:** add base-modal-container component ([b0e5083](https://github.com/empathyco/x/commit/b0e5083ca9725f6ae21a7934d4479ee5870e7d65)), closes [EX-1765](https://searchbroker.atlassian.net/browse/EX-1765)
* **base-modal:** add an overlay layer to `BaseModal` component listening to click events outside the modal to close it ([20ced42](https://github.com/empathyco/x/commit/20ced42df84f4857291e836512c25711e0fa6772)), closes [EX-3786](https://searchbroker.atlassian.net/browse/EX-3786)
* **base-modal:** migrate base-modal component and side effects (#1479) ([610ec16](https://github.com/empathyco/x/commit/610ec16e20b10a344936b2914c61085e22a09dfd))
* **base-rating-filter-title:** add base rating filter title component ([0562702](https://github.com/empathyco/x/commit/05627022db8f9dc0da5841c74cc823e0bb82d9bc)), closes [EX-2832](https://searchbroker.atlassian.net/browse/EX-2832)
* **base-rating:** added base rating component ([1cf82e5](https://github.com/empathyco/x/commit/1cf82e57179048ea4c424e793d177b8f9720aab9)), closes [EX-2871](https://searchbroker.atlassian.net/browse/EX-2871)
* **base-result-current-price:** created base result current price component ([7544c19](https://github.com/empathyco/x/commit/7544c1984253f26a8824defcdafab6d767735aa1)), closes [EX-1913](https://searchbroker.atlassian.net/browse/EX-1913)
* **base-result-image:** Added the base result image with lazy loading also fallback and placeholder ([d23cc1e](https://github.com/empathyco/x/commit/d23cc1e32a126ee25468f7cf70000bd6c6ac8f35))
* **base-result-link:** refactor BaseResultLink component to receive origin and events by injection ([139da7a](https://github.com/empathyco/x/commit/139da7a92cb6e66893f25681554b8f07b142965a)), closes [EX-1971](https://searchbroker.atlassian.net/browse/EX-1971)
* **base-result-previous-price:** added base result previous price component ([82c9965](https://github.com/empathyco/x/commit/82c9965fd0b94193884cda5ab310a18261748390)), closes [EX-1913](https://searchbroker.atlassian.net/browse/EX-1913)
* **base-show-more:** new component for showing more filters ([b58f253](https://github.com/empathyco/x/commit/b58f25392ff5598b376732904ea80a4c1e44942e)), closes [EX-2721](https://searchbroker.atlassian.net/browse/EX-2721)
* **base-suggestion:** allow string in matching part to retain accent marks ([edf6fbf](https://github.com/empathyco/x/commit/edf6fbf5e9bc7950d52c0304d891275807c78c10)), closes [EX-1886](https://searchbroker.atlassian.net/browse/EX-1886)
* **base-suggestions:** add index to slot bindings for suggestions ([67b78fb](https://github.com/empathyco/x/commit/67b78fbc104175564bd74e032b423c805b8acd26)), closes [EX-1966](https://searchbroker.atlassian.net/browse/EX-1966)
* **build:** add rollup polyfills wrapper plugin ([2686947](https://github.com/empathyco/x/commit/2686947f81337f808ac1fbfb1e493f8ff3bc6498)), closes [EX-2051](https://searchbroker.atlassian.net/browse/EX-2051)
* **bus:** make `useXBus` get bus from `XPlugin` (#1447) ([c57d1af](https://github.com/empathyco/x/commit/c57d1aff8df162e5b99b78822ba5013b617d4aba))
* **bus:** make metadata parameter optional ([61d5701](https://github.com/empathyco/x/commit/61d570174dd5e19812226833a0aea7fc1e9ef7e6)), closes [EX-1695](https://searchbroker.atlassian.net/browse/EX-1695)
* **cancellable-promise:** add cancellable-promise utility ([1adcf09](https://github.com/empathyco/x/commit/1adcf098ecde9bec64404b3504aefd6d6610e676)), closes [EX-2244](https://searchbroker.atlassian.net/browse/EX-2244)
* change all dynamic slots to kebab-case ([039d524](https://github.com/empathyco/x/commit/039d524d52b48019a02d31303fd23b59f19eee68)), closes [EX-4807](https://searchbroker.atlassian.net/browse/EX-4807)
* Change suggestion components to bind $attrs to base suggestions (#831) ([49c139b](https://github.com/empathyco/x/commit/49c139bc55f4cc1a2e1e0ec2e2e7972376eaf487)), closes [EX-7356](https://searchbroker.atlassian.net/browse/EX-7356)
* change useHybridInject so it works more like vue inject (#1427) ([f7e2946](https://github.com/empathyco/x/commit/f7e2946771213c06b6b7f6c9b4987ba971303463))
* **clear-search-input:** add clear-search-input button ([3fa6de6](https://github.com/empathyco/x/commit/3fa6de641812e513fdb6a6e34298cb929a5e595e)), closes [EX-1663](https://searchbroker.atlassian.net/browse/EX-1663)
* **close-button:** add close-button component ([7e217e3](https://github.com/empathyco/x/commit/7e217e304d021a34e6933aea2ab63e2e49daa36d)), closes [EX-1765](https://searchbroker.atlassian.net/browse/EX-1765)
* **compile-message:** add compileMessage filter and register it globally ([2663260](https://github.com/empathyco/x/commit/26632604d519130fa139f4d91924cdb01316b238)), closes [EX-1779](https://searchbroker.atlassian.net/browse/EX-1779)
* **components:** add  `columns` prop in `BaseVariableColumnGrid` (#1112) ([8a74847](https://github.com/empathyco/x/commit/8a7484779542768a1f03dbd09eff164b0ecb8686)), closes [EX-8135](https://searchbroker.atlassian.net/browse/EX-8135)
* **components:** Add `@XEmit` decorator ([a753cf1](https://github.com/empathyco/x/commit/a753cf18346d3f99799da478ada3348645b7af84)), closes [EX-4245](https://searchbroker.atlassian.net/browse/EX-4245)
* **components:** add `BaseDropdown` component. ([b5d94e4](https://github.com/empathyco/x/commit/b5d94e4025f6c1a75bc36a995697f545570dbcef))
* **components:** add `BaseSwitch` component (#586) ([31cde2d](https://github.com/empathyco/x/commit/31cde2dfb79dcc549c8662b558ef5b80529f2d01)), closes [EX-6004](https://searchbroker.atlassian.net/browse/EX-6004)
* **components:** add `BaseVariableColumnGrid` component ([5bb8b66](https://github.com/empathyco/x/commit/5bb8b66040b766323fd4fb7d93ac62282d56b8a3)), closes [EX-3297](https://searchbroker.atlassian.net/browse/EX-3297)
* **components:** add `buttonClass` prop in `SlidingPanel` ([fa554a2](https://github.com/empathyco/x/commit/fa554a2231ec9a00b5aea566970c2b7b0d34845f)), closes [EX-5233](https://searchbroker.atlassian.net/browse/EX-5233)
* **components:** add `contentClass` to `modals` (#1009) ([68b8790](https://github.com/empathyco/x/commit/68b8790289dd6e233c0199497cdb09f515ccbeec)), closes [EX-7479](https://searchbroker.atlassian.net/browse/EX-7479)
* **components:** add `getTargetElement` util to retrieve the `event.target` (#870) ([8be7beb](https://github.com/empathyco/x/commit/8be7beba25a5a90b142fbb1a905d41503befc92c))
* **components:** Add `GlobalXBus `component ([cc8e28b](https://github.com/empathyco/x/commit/cc8e28b5b5d7f1735c490c0b576d620f4f1dd103)), closes [EX-3535](https://searchbroker.atlassian.net/browse/EX-3535)
* **components:** add `LocationProvider` component ([b005713](https://github.com/empathyco/x/commit/b0057130d99767efebcd8da6ef669bee81bac567)), closes [EX-4639](https://searchbroker.atlassian.net/browse/EX-4639)
* **components:** add `MainModal`, `OpenMainModal` and `CloseMainModal` (#609) ([526ab58](https://github.com/empathyco/x/commit/526ab5813f58258180b5640cab6bf0f2179fa40a)), closes [EX-6546](https://searchbroker.atlassian.net/browse/EX-6546)
* **components:** Add `payload` and `metadata` to the `SnippetCallbackExecuted` event payload ([a18b8fa](https://github.com/empathyco/x/commit/a18b8fafcc7607fef82d3c9fb1211669f3bbc8a3)), closes [EX-5324](https://searchbroker.atlassian.net/browse/EX-5324)
* **components:** add `SnippetCallbacks` component ([0b89a9f](https://github.com/empathyco/x/commit/0b89a9ff0de60194567d47e768bf0f0fb654b998)), closes [EX-5002](https://searchbroker.atlassian.net/browse/EX-5002)
* **components:** Add `TranslateFromLeft` and `CrossFade` animations. ([7690dcd](https://github.com/empathyco/x/commit/7690dcdd1b3286b36584a18de5141038aaa1597d)), closes [EX-4772](https://searchbroker.atlassian.net/browse/EX-4772)
* **components:** add AnimateWidth animation component ([c9c78c6](https://github.com/empathyco/x/commit/c9c78c6f71e30881f741b1f32543e139db71c28e)), closes [EX-4107](https://searchbroker.atlassian.net/browse/EX-4107)
* **components:** add base-hierarchical-filter component. ([f1bb593](https://github.com/empathyco/x/commit/f1bb593609bb8541507ee8c5e387df47c4fd4f5b))
* **components:** add BaseIdScroll component ([8ae6e53](https://github.com/empathyco/x/commit/8ae6e536a6e3975781c4a2607bae6f2529223220)), closes [EX-3387](https://searchbroker.atlassian.net/browse/EX-3387)
* **components:** add BaseMainScroll component ([265360e](https://github.com/empathyco/x/commit/265360e86d6d86f2f0851dd0ca158c766f69c741)), closes [EX-3193](https://searchbroker.atlassian.net/browse/EX-3193)
* **components:** add disable animation mixin (#703) ([ea344f9](https://github.com/empathyco/x/commit/ea344f9d5e7b36da6aabdd4fe5d2a1ad05dbcfc8)), closes [EX-6838](https://searchbroker.atlassian.net/browse/EX-6838)
* **components:** add filters to base-suggestions (#758) ([2014861](https://github.com/empathyco/x/commit/2014861453215808ee4279f9484f1d845780d7bf)), closes [EX-6346](https://searchbroker.atlassian.net/browse/EX-6346)
* **components:** add grid-4-col and update light-bulb icons (#579) ([5312952](https://github.com/empathyco/x/commit/5312952c69f67525a35b77008128264eddaae206)), closes [EX-6506](https://searchbroker.atlassian.net/browse/EX-6506)
* **components:** Add icons for Arrows UP DOWN LEFT and RIGHT. (#295) ([693b26f](https://github.com/empathyco/x/commit/693b26f8e2d250f97bcf0cce472299b2edcc4823)), closes [EX-5245](https://searchbroker.atlassian.net/browse/EX-5245)
* **components:** add mixing `CollapseWidth` component export ([5e07c48](https://github.com/empathyco/x/commit/5e07c4843899842afa7e6a172a7f48f2aaa6c627)), closes [EX-2994](https://searchbroker.atlassian.net/browse/EX-2994)
* **components:** add new fixed header and aside layout ([e2c0ed5](https://github.com/empathyco/x/commit/e2c0ed5ad2ea0015b7d6d330d97499ad64d8947c)), closes [EX-4821](https://searchbroker.atlassian.net/browse/EX-4821)
* **components:** add new modals components ([dfcbb40](https://github.com/empathyco/x/commit/dfcbb4005ea7fe685570368d16bf6cb0ab716d53)), closes [EX-2830](https://searchbroker.atlassian.net/browse/EX-2830)
* **components:** Add new origins to the `animateClipPath` animation factory. (#777) ([d016057](https://github.com/empathyco/x/commit/d016057ea0c92901dc88df755351b4acee32f472)), closes [EX-7195](https://searchbroker.atlassian.net/browse/EX-7195)
* **components:** add new slot `extra-aside` to `SingleColumnLayout` and `FixedHeaderAndAsidesLayout` (#591) ([91d406e](https://github.com/empathyco/x/commit/91d406ed7267d420009a5f3ee8c5cc092f74546a)), closes [EX-6614](https://searchbroker.atlassian.net/browse/EX-6614)
* **components:** add option to hide decimals if the number to format is an integer in `currencyFormatter` `format` option. ([b2f6450](https://github.com/empathyco/x/commit/b2f64507f3ce4713c9ed1df725a2c84c01c21f78)), closes [EX-3547](https://searchbroker.atlassian.net/browse/EX-3547)
* **components:** add radio button icons (#574) ([4432d5f](https://github.com/empathyco/x/commit/4432d5f927e5c5cac6cb7481923e32ceb6cb0499)), closes [EX-6439](https://searchbroker.atlassian.net/browse/EX-6439)
* **components:** add Result Rating component ([db5cbb5](https://github.com/empathyco/x/commit/db5cbb5779e0e503ec934df4cda3dd241c49fc8e)), closes [EX-5243](https://searchbroker.atlassian.net/browse/EX-5243)
* **components:** Allow `BaseResultAddToCart` to use external listeners. ([a596c07](https://github.com/empathyco/x/commit/a596c07c1ead0e8d3fcf169afddaf15ad6d92e47)), closes [EX-5323](https://searchbroker.atlassian.net/browse/EX-5323)
* **components:** change the render conditions in the Layout component ([7853adc](https://github.com/empathyco/x/commit/7853adc65112e687f6f6083407b1259494cc72a9)), closes [EX-4171](https://searchbroker.atlassian.net/browse/EX-4171)
* **components:** composable and component to fire callbacks when an element appears on viewport (#1391) ([c463352](https://github.com/empathyco/x/commit/c46335243c74c604e6f8168c158461edff9d4eb5))
* **components:** create component clear all filters ([74f68de](https://github.com/empathyco/x/commit/74f68def1a7a077fcee1a50d29525a7b903760f2)), closes [EX-2560](https://searchbroker.atlassian.net/browse/EX-2560)
* **components:** create useStore composable (#1401) ([b4e42b9](https://github.com/empathyco/x/commit/b4e42b95bdee4dcc869908e9505830cc15e975a8))
* **components:** created abstract factory for animations ([a6120c1](https://github.com/empathyco/x/commit/a6120c135f93e5993f8d41b2b823085a2bf3d291)), closes [EX-5355](https://searchbroker.atlassian.net/browse/EX-5355)
* **components:** deprecate x-picture__image and placeholder/fallback styles (#1036) ([73a08a5](https://github.com/empathyco/x/commit/73a08a576b3f9b715cccefee8cb452d00cd45bcb)), closes [EX-7888](https://searchbroker.atlassian.net/browse/EX-7888)
* **components:** Emit ColumnsNumberRendered event on BaseGrid (#806) ([87a8ca9](https://github.com/empathyco/x/commit/87a8ca947f8d83dff1a0044db80649eb297361fb)), closes [EX-7291](https://searchbroker.atlassian.net/browse/EX-7291)
* **components:** fix 'BaseRating' component styles (#264) ([053447f](https://github.com/empathyco/x/commit/053447fdb2884f04f6099b6b78876c006568a644)), closes [EX-5096](https://searchbroker.atlassian.net/browse/EX-5096)
* **components:** insert promoteds in the grid using position (#801) ([b537cae](https://github.com/empathyco/x/commit/b537caeb2077fa6b8d5898d0dbdb9069a06ab2e8)), closes [EX-7295](https://searchbroker.atlassian.net/browse/EX-7295)
* **components:** make `BaseIdModalClose` rendering configurable (#627) ([4bf97af](https://github.com/empathyco/x/commit/4bf97af19ac5f2fd1b08b6e4097dec45eef00679)), closes [EX-6726](https://searchbroker.atlassian.net/browse/EX-6726)
* **components:** make `BaseIdModalOpen` rendering configurable (#637) ([77cb564](https://github.com/empathyco/x/commit/77cb5646b1e43c8b7aa428db4102dc6aca8affdf)), closes [EX-6751](https://searchbroker.atlassian.net/browse/EX-6751)
* **components:** merge a variant with the result (#667) ([553d0e5](https://github.com/empathyco/x/commit/553d0e5de8ef5468eb673246f39fbeb826301fa1)), closes [EX-6762](https://searchbroker.atlassian.net/browse/EX-6762)
* **components:** move `maxItemsToRender` prop to `BaseSuggestions`. Add `maxItemsToRender` prop to `Recommendations`. ([f26a189](https://github.com/empathyco/x/commit/f26a189a60f697579bf4334b899a701def05a22a)), closes [EX-3993](https://searchbroker.atlassian.net/browse/EX-3993)
* **components:** remove deprecated origins (#1355) ([3d7c981](https://github.com/empathyco/x/commit/3d7c981380bd8af30724780f7810808d563db471))
* **components:** replace `BaseEventButton` for an html button ([6028f16](https://github.com/empathyco/x/commit/6028f16374b794df9233a9aada78933502873864)), closes [EX-5003](https://searchbroker.atlassian.net/browse/EX-5003)
* **components:** Use `Highlight` component inside suggestion components.(#894) ([ceb9c0c](https://github.com/empathyco/x/commit/ceb9c0c729d9a7a3b8a983e5b23912d561f2bd4d)), closes [EX-7469](https://searchbroker.atlassian.net/browse/EX-7469)
* **components:** use XDS `sliding panel` (#1028) ([9773003](https://github.com/empathyco/x/commit/97730036b473678b8487a386bc6d83bd3ecf872d)), closes [EX-7831](https://searchbroker.atlassian.net/browse/EX-7831)
* **components:** variants auto selection (#679) ([c1c8664](https://github.com/empathyco/x/commit/c1c866481ae8866fec4fd9e2dd5389fcba00e62b)), closes [EX-6878](https://searchbroker.atlassian.net/browse/EX-6878)
* **composables:** create use getter composable (#1407) ([44a1488](https://github.com/empathyco/x/commit/44a148848ab027a624a3a1980ed4a62cb0956dea))
* **composables:** create useState composable (#1402) ([435af42](https://github.com/empathyco/x/commit/435af4222a2ed08d44d728a973406c0e1122b862))
* **composables:** create XBus composable (#1412) ([5246135](https://github.com/empathyco/x/commit/5246135aaf2581e338dcf1934aeb8fb781cfe0a0))
* **config:** refactor XPluginOptions and XModule configurations ([344a91b](https://github.com/empathyco/x/commit/344a91b12d7a97115524860d7974c98c3f6cd764)), closes [EX-1994](https://searchbroker.atlassian.net/browse/EX-1994)
* **contributing-guide:** Add contributing guide ([24930aa](https://github.com/empathyco/x/commit/24930aa470cb1985b031158e7a9fc00f886339ee)), closes [EX-2891](https://searchbroker.atlassian.net/browse/EX-2891)
* **conventional-commits:** Add conventional-commits and commitizen npm packages ([2d8b021](https://github.com/empathyco/x/commit/2d8b021dc54eaf51b915539db81f38b2bbef48aa)), closes [EX-1614](https://searchbroker.atlassian.net/browse/EX-1614)
* Create experience controls module tests (#1303) ([98acc0f](https://github.com/empathyco/x/commit/98acc0f68a184f6774acb1f8f6506ec9f5d1ed48))
* create load next page component (#1424) ([cf05167](https://github.com/empathyco/x/commit/cf05167904dfdc018e36f33c7d0df2ff0e5de4a9))
* **create-animation:** migrate to composition API (#1553) ([1097c0d](https://github.com/empathyco/x/commit/1097c0d1b9dd63f9573812b9ddb41b790725b46e))
* creating useRegisterXModule composable (#1399) ([850a741](https://github.com/empathyco/x/commit/850a741f3a144ae79374d85e7e2f6a2f1c502946))
* **currency-filter:** add currency filter and formatter ([324ee6b](https://github.com/empathyco/x/commit/324ee6ba6e09ff50840157943a4220c042e584bb)), closes [EX-1913](https://searchbroker.atlassian.net/browse/EX-1913)
* **currency:** crate a title component for currency ([d3a010d](https://github.com/empathyco/x/commit/d3a010d9ca67503e4e261f1847b78ae177d769c0)), closes [EX-2759](https://searchbroker.atlassian.net/browse/EX-2759)
* **cypress:** add @cypress/webpack-preprocessor to support TypeScript ([39c04cc](https://github.com/empathyco/x/commit/39c04cc1f6b8a405e151aa7cbabe27174a2bb4a0)), closes [EX-1790](https://searchbroker.atlassian.net/browse/EX-1790)
* **cypress:** add custom command for cypress ([33a0b14](https://github.com/empathyco/x/commit/33a0b1476fd818ad8aca01bb83a1e855b33a70c7)), closes [EX-1792](https://searchbroker.atlassian.net/browse/EX-1792)
* **cypress:** disable video recording in Cypress e2e tests ([096754f](https://github.com/empathyco/x/commit/096754f93bcd42eead17c35aea127020a28913a1)), closes [EX-1866](https://searchbroker.atlassian.net/browse/EX-1866)
* **cypress:** inject XComponents to the global window object when Cypress is running ([b968661](https://github.com/empathyco/x/commit/b968661eaba97548346c16d84f7ec70034466e47)), closes [EX-1768](https://searchbroker.atlassian.net/browse/EX-1768)
* **decorator:** add support for multiple and dynamic events to XOn decorator ([e2a1ea4](https://github.com/empathyco/x/commit/e2a1ea422c2e3c1a08123592eaeb99e8d666010c)), closes [EX-1977](https://searchbroker.atlassian.net/browse/EX-1977)
* **decorators:** add `@XProvide` and `@XInject` decorators ([8d23e0d](https://github.com/empathyco/x/commit/8d23e0db4469a151e9550e18abbbaec8115bbad4)), closes [EX-2893](https://searchbroker.atlassian.net/browse/EX-2893)
* **decorators:** add filtering support to XOn decorator ([4b8221e](https://github.com/empathyco/x/commit/4b8221e683467323f30f0e1ff35da2d33ec3b578)), closes [EX-1874](https://searchbroker.atlassian.net/browse/EX-1874)
* **design-system:** add `curated` modifier to the `suggestion` ([dd229fd](https://github.com/empathyco/x/commit/dd229fd3d64840ed3041bec618a1a23e3726430d)), closes [EX-5290](https://searchbroker.atlassian.net/browse/EX-5290)
* **design-system:** add `icon` to XDS  (#1053) ([21605ab](https://github.com/empathyco/x/commit/21605abc99f5da05556cfa7edb4213c61c205b78)), closes [EX-7783](https://searchbroker.atlassian.net/browse/EX-7783)
* **design-system:** Add `Input Group` component to the X Desing System. (#1066) ([5f83b14](https://github.com/empathyco/x/commit/5f83b1460408e0e3b6a5f7fedaf91ee006d27a9c)), closes [EX-7944](https://searchbroker.atlassian.net/browse/EX-7944)
* **design-system:** add `input-group` variants ([5fba8b0](https://github.com/empathyco/x/commit/5fba8b0ee3477c6f0161a754ac385f94065eecba)), closes [EX-3707](https://searchbroker.atlassian.net/browse/EX-3707)
* **design-system:** add `justified` variant to `x-filter` component ([236fabe](https://github.com/empathyco/x/commit/236fabed364a9bf8e8d015587d12f019c27be506)), closes [EX-3874](https://searchbroker.atlassian.net/browse/EX-3874)
* **design-system:** add `product-image` `XDS` component (#1025) ([d60e239](https://github.com/empathyco/x/commit/d60e239012d04d547b5430eb8afc22536f66d838))
* **design-system:** add `Shadow` component ([2592a4d](https://github.com/empathyco/x/commit/2592a4d9975109b0733a550c7d40f271ec984456)), closes [EX-4739](https://searchbroker.atlassian.net/browse/EX-4739)
* **design-system:** add `SingleColumnLayout` component. ([97f3000](https://github.com/empathyco/x/commit/97f3000ff024c0d46ce06099babc0ed17bc6ebe2)), closes [EX-4706](https://searchbroker.atlassian.net/browse/EX-4706)
* **design-system:** add `SlidingPanel` default CSS and tokens ([832485e](https://github.com/empathyco/x/commit/832485e93800c30824af9f69fce1f3b6094235fb)), closes [EX-3864](https://searchbroker.atlassian.net/browse/EX-3864)
* **design-system:** add `suggestion` component to the XDS (#838) ([055af83](https://github.com/empathyco/x/commit/055af838ddbf3a1293936d5994c455e4e8499654))
* **design-system:** add `tailwindcss` to `x-components` and configure it to use `x-tailwindcss` (#655) ([4109a8a](https://github.com/empathyco/x/commit/4109a8ad9d29378078603d97e31c073ceb2671ae)), closes [EX-6793](https://searchbroker.atlassian.net/browse/EX-6793)
* **design-system:** add `x-button--ghost-start` and `x-button--ghost-end` modifiers to `x-button--ghost` variant ([8150136](https://github.com/empathyco/x/commit/81501363c99e52e772b917b528162f116c4dd4b1)), closes [EX-4179](https://searchbroker.atlassian.net/browse/EX-4179)
* **design-system:** add `x-button` css class in the necessary elements ([f100168](https://github.com/empathyco/x/commit/f1001687534eefd7885b57808fc75bd12f25337d)), closes [EX-3703](https://searchbroker.atlassian.net/browse/EX-3703)
* **design-system:** add `x-filter` tokens and CSS ([0e26d32](https://github.com/empathyco/x/commit/0e26d321b7ef946fd160e08dbe3ea9b84197ecfa)), closes [EX-3767](https://searchbroker.atlassian.net/browse/EX-3767)
* **design-system:** add `x-scroll` component and tokens ([99243d1](https://github.com/empathyco/x/commit/99243d108eca3e9d4479f241fe7472df5d2dd9d0)), closes [EX-4085](https://searchbroker.atlassian.net/browse/EX-4085)
* **design-system:** add `x-suggestion` design tokens ([90866e8](https://github.com/empathyco/x/commit/90866e8051f46ff6229f2a1a6ca6bb8b9bb0e7a6)), closes [EX-3715](https://searchbroker.atlassian.net/browse/EX-3715)
* **design-system:** add `x-tag` variants tokens and CSS styles ([574619e](https://github.com/empathyco/x/commit/574619e9c9f4d253689c6ff3acc06fb7dce3300c)), closes [EX-3916](https://searchbroker.atlassian.net/browse/EX-3916)
* **design-system:** add base tokens ([f13a9a9](https://github.com/empathyco/x/commit/f13a9a9e707f32916b240b4ab76e73257b827851)), closes [EX-3672](https://searchbroker.atlassian.net/browse/EX-3672)
* **design-system:** Add bottom variant to `x-shadow` utility in the Design System ([a23552f](https://github.com/empathyco/x/commit/a23552f29d1ec1b7939c770862d91f9e2f3a4890)), closes [EX-5184](https://searchbroker.atlassian.net/browse/EX-5184)
* **design-system:** add Button variations tokens and CSS ([0b26585](https://github.com/empathyco/x/commit/0b2658540c846bb6ad5e17385b44c5ec3aa379bf)), closes [EX-3689](https://searchbroker.atlassian.net/browse/EX-3689)
* **design-system:** add curated tags (#311) ([9f40c2b](https://github.com/empathyco/x/commit/9f40c2b17eb08353efc964dba075470877eead46)), closes [EX-5089](https://searchbroker.atlassian.net/browse/EX-5089)
* **design-system:** add default `x-facet` tokens and CSS and `x-icon` variants ([0b75d6e](https://github.com/empathyco/x/commit/0b75d6eb70da5a0809b478eba413dafdc2ade343)), closes [EX-3881](https://searchbroker.atlassian.net/browse/EX-3881)
* **design-system:** add default button design tokens and styles ([8388e45](https://github.com/empathyco/x/commit/8388e4518b0dab926449ac7eabfc121c28cfc91a)), closes [EX-3688](https://searchbroker.atlassian.net/browse/EX-3688)
* **design-system:** add Design System classes for the picture image fallback and placeholder ([61494d4](https://github.com/empathyco/x/commit/61494d4a952eff898aa6a58a5eb908b965f3d5a4)), closes [EX-4070](https://searchbroker.atlassian.net/browse/EX-4070)
* **design-system:** add design system icons ([a904c11](https://github.com/empathyco/x/commit/a904c1103c95d0fa417086f7004e90acf188898e)), closes [EX-3973](https://searchbroker.atlassian.net/browse/EX-3973)
* **design-system:** add Design System view as showcase ([1d7df92](https://github.com/empathyco/x/commit/1d7df922eb3c9f5f5ff6762e395653bd4e6c5b69)), closes [EX-3690](https://searchbroker.atlassian.net/browse/EX-3690)
* **design-system:** Add Desing System Message and Progress Bar components ([bba13c9](https://github.com/empathyco/x/commit/bba13c9b632bbe6dad40505bcd5382bfd2105f8e)), closes [EX-4904](https://searchbroker.atlassian.net/browse/EX-4904)
* **design-system:** add direction Border and Padding List variants ([20f5640](https://github.com/empathyco/x/commit/20f564094569501f83da0a003e8c2f04cab64722)), closes [EX-4064](https://searchbroker.atlassian.net/browse/EX-4064)
* **design-system:** add dropdown design tokens ([0a1d239](https://github.com/empathyco/x/commit/0a1d2397926f3f52b64e5f8ef3c212bf9e44438f)), closes [EX-3769](https://searchbroker.atlassian.net/browse/EX-3769)
* **design-system:** add dropdown size variants ([f099c73](https://github.com/empathyco/x/commit/f099c7354133407b55d69286439aa5d92c1bad80)), closes [EX-4098](https://searchbroker.atlassian.net/browse/EX-4098)
* **design-system:** add icons to the Design System view ([d929922](https://github.com/empathyco/x/commit/d92992277d5c917f4b4ef56aec8837fc5879dae8)), closes [EX-4110](https://searchbroker.atlassian.net/browse/EX-4110)
* **design-system:** add identifier result in suggestion component ([d4ce3c2](https://github.com/empathyco/x/commit/d4ce3c2eb1188e38e55e466f65c9da165bf9bfe7)), closes [EX-5065](https://searchbroker.atlassian.net/browse/EX-5065)
* **design-system:** add input default tokens and CSS ([496cb73](https://github.com/empathyco/x/commit/496cb73612506419be9b6a012de0418ca890b9cd)), closes [EX-3694](https://searchbroker.atlassian.net/browse/EX-3694)
* **design-system:** add input variants tokens and CSS ([977df04](https://github.com/empathyco/x/commit/977df04ac3c80eaa34bd20e331f13f418863db61)), closes [EX-3696](https://searchbroker.atlassian.net/browse/EX-3696)
* **design-system:** add Layout component and Design System Layout component ([84880a1](https://github.com/empathyco/x/commit/84880a1d36631d99f4946533cfc88cd1e66b3032)), closes [EX-3866](https://searchbroker.atlassian.net/browse/EX-3866)
* **design-system:** add list design tokens ([b4dfbd8](https://github.com/empathyco/x/commit/b4dfbd8b99fbd9e2bb64df8cf1138d67daf635df)), closes [EX-3925](https://searchbroker.atlassian.net/browse/EX-3925)
* **design-system:** add lists background colors to Design System ([9d23d61](https://github.com/empathyco/x/commit/9d23d6145d3a6ac12f0553af5ced2c5cc9c68653)), closes [EX-4695](https://searchbroker.atlassian.net/browse/EX-4695)
* **design-system:** Add more utility classes.  ([592e076](https://github.com/empathyco/x/commit/592e0761d201d80fdf62ba260ac4ef0847fb7f17)), closes [EX-5241](https://searchbroker.atlassian.net/browse/EX-5241)
* **design-system:** add more values to the `x-list` variants ([5efa573](https://github.com/empathyco/x/commit/5efa573510c89aed508e1a0cbad74fdc0b9d1429)), closes [EX-4174](https://searchbroker.atlassian.net/browse/EX-4174)
* **design-system:** add new typography variants ([94c5d40](https://github.com/empathyco/x/commit/94c5d40f1402916b64290101c33f4a1d174b3e8b)), closes [EX-4092](https://searchbroker.atlassian.net/browse/EX-4092)
* **design-system:** add option list tokens ([a99b2ad](https://github.com/empathyco/x/commit/a99b2add7fc6980f0b41c3c03b082429f530d853)), closes [EX-3860](https://searchbroker.atlassian.net/browse/EX-3860)
* **design-system:** add scroll-to-top slot in Layout ([421e937](https://github.com/empathyco/x/commit/421e9371da6f84069ae033cf0cba8ef360c2603e)), closes [EX-4192](https://searchbroker.atlassian.net/browse/EX-4192)
* **design-system:** Add suggestion group component (#943) ([4bac818](https://github.com/empathyco/x/commit/4bac8183a29ec17a99a90edeae55ba3d4301b626)), closes [EX-7496](https://searchbroker.atlassian.net/browse/EX-7496)
* **design-system:** add tags default tokens and CSS ([433c880](https://github.com/empathyco/x/commit/433c8801e771cd9dd9c4b5f39bf75a9bb1539e97)), closes [EX-3771](https://searchbroker.atlassian.net/browse/EX-3771)
* **design-system:** add tailwind showcase component (#778) ([0178ef5](https://github.com/empathyco/x/commit/0178ef5a4b472e2ca14f98f1243d08e36e1f5840)), closes [EX-7078](https://searchbroker.atlassian.net/browse/EX-7078)
* **design-system:** add the `.x-input` class to the XComponents where necessary ([2f4d902](https://github.com/empathyco/x/commit/2f4d90255eb7aa328117a5b09baddbbfb3a6a8be)), closes [EX-3712](https://searchbroker.atlassian.net/browse/EX-3712)
* **design-system:** add tokens for non matching part of suggestion ([550f2f4](https://github.com/empathyco/x/commit/550f2f42940019b3108fb4a83c88fc668a1f47e1)), closes [EX-4786](https://searchbroker.atlassian.net/browse/EX-4786)
* **design-system:** add utilities ([cc5c6cc](https://github.com/empathyco/x/commit/cc5c6cc2eb2daf48cf06c968a06465bb19ff89d9)), closes [EX-4746](https://searchbroker.atlassian.net/browse/EX-4746)
* **design-system:** add x-facet variants tokens and CSS styles ([ffc706b](https://github.com/empathyco/x/commit/ffc706b3228eda852f921706a37ee3ce72aefbcd)), closes [EX-3914](https://searchbroker.atlassian.net/browse/EX-3914)
* **design-system:** add x-grid Design System tokens ([398ba0e](https://github.com/empathyco/x/commit/398ba0e84180fbc14ce3f71d001564867f22ab1c)), closes [EX-4082](https://searchbroker.atlassian.net/browse/EX-4082)
* **design-system:** add x-result Design System tokens ([9fa7067](https://github.com/empathyco/x/commit/9fa7067dd004341259f0e00194c4b107df0ccc34)), closes [EX-3765](https://searchbroker.atlassian.net/browse/EX-3765)
* **design-system:** add x-tag css class in the necessary elements ([74c17ca](https://github.com/empathyco/x/commit/74c17cab6c54bd31e98beb91d1f10a219f03ac79)), closes [EX-3912](https://searchbroker.atlassian.net/browse/EX-3912)
* **design-system:** add XDS badge component (#1100) ([c0d8446](https://github.com/empathyco/x/commit/c0d84461b1cb72705e8570766c19078c2eef3abf)), closes [EX-7992](https://searchbroker.atlassian.net/browse/EX-7992)
* **design-system:** add XDS progress bar component (#1149) ([21a52f5](https://github.com/empathyco/x/commit/21a52f5b3af3f4ac341e3b9844e0273b355153aa))
* **design-system:** add zoom effect (#799) ([e7af33a](https://github.com/empathyco/x/commit/e7af33a7d2186e4fc6191961ee8b12a35198fc59)), closes [EX-6315](https://searchbroker.atlassian.net/browse/EX-6315)
* **design-system:** allow suggestions to be tags ([24c94bb](https://github.com/empathyco/x/commit/24c94bb604f87a2135a36be5a298f053eba80738)), closes [EX-4917](https://searchbroker.atlassian.net/browse/EX-4917)
* **design-system:** change curated tag toke values to reuse default ones. ([2fd261a](https://github.com/empathyco/x/commit/2fd261ae54ec3de8eabdbcd5611bf5e1416d37f8)), closes [EX-5354](https://searchbroker.atlassian.net/browse/EX-5354)
* **design-system:** deprecate old design system button styles (#830) ([78fbf63](https://github.com/empathyco/x/commit/78fbf63116a9312e361540388b2573e0939dc7ae))
* **design-system:** deprecate old DS (#1138) ([53b0558](https://github.com/empathyco/x/commit/53b05585551a07548bf8071d5112b94f4151544b))
* **design-system:** deprecate old DS `Tag` component (#1103) ([f698e00](https://github.com/empathyco/x/commit/f698e004daa0ed73fafefa2968c2b1ced66397e7)), closes [EX-7990](https://searchbroker.atlassian.net/browse/EX-7990)
* **design-system:** deprecate old DS filters (#1121) ([dd9690d](https://github.com/empathyco/x/commit/dd9690d5f59ae39e6c7f1a29f542732c03221cfe)), closes [EX-8152](https://searchbroker.atlassian.net/browse/EX-8152)
* **design-system:** deprecate old suggestion and suggestion group styles (#975) ([69d8bc5](https://github.com/empathyco/x/commit/69d8bc59ce43660b3295dcafa9283598d1143336)), closes [EX-7725](https://searchbroker.atlassian.net/browse/EX-7725)
* **design-system:** deprecate old typography styles (#973) ([15d6d64](https://github.com/empathyco/x/commit/15d6d64c18fe28664e873802fe34073158c30648)), closes [EX-7726](https://searchbroker.atlassian.net/browse/EX-7726)
* **design-system:** deprecate old x-scroll styles (#1073) ([3916c5f](https://github.com/empathyco/x/commit/3916c5fab866a51f5c2df089cef3e80a9c0ae1ee)), closes [EX-7982](https://searchbroker.atlassian.net/browse/EX-7982)
* **design-system:** generate old design system tokens with tailwind values (#675) ([7aa42e4](https://github.com/empathyco/x/commit/7aa42e4e26ec34fea942bbf7f0c7f10a97a94237)), closes [EX-6790](https://searchbroker.atlassian.net/browse/EX-6790)
* **design-system:** improve `x-icon` token ([7057737](https://github.com/empathyco/x/commit/70577378197372f33378c2a4bf40334d01168cf3)), closes [EX-4017](https://searchbroker.atlassian.net/browse/EX-4017)
* **design-system:** refactor styles folder structure ([218fbe1](https://github.com/empathyco/x/commit/218fbe1c1c873e69e33515aa9253db08070e89fe)), closes [EX-3822](https://searchbroker.atlassian.net/browse/EX-3822)
* **design-tokens:** add `x-row` and `x-row-item` tokens ([6aecf08](https://github.com/empathyco/x/commit/6aecf086de7368925d012207064badf65a3d9198)), closes [EX-4000](https://searchbroker.atlassian.net/browse/EX-4000)
* **design-tokens:** add result image design tokens ([227a4ae](https://github.com/empathyco/x/commit/227a4ae8757b5c69d56387f8df7b78591b35cb1c)), closes [EX-3977](https://searchbroker.atlassian.net/browse/EX-3977)
* **desing-system:** Add `Grid2RowsIcon` component ([cbd014f](https://github.com/empathyco/x/commit/cbd014fb1a07c2aa738c3ef828c9caf5ec9ded39)), closes [EX-5238](https://searchbroker.atlassian.net/browse/EX-5238)
* **desing-system:** add `hierarchical` variant to `x-filter` ([ed399b6](https://github.com/empathyco/x/commit/ed399b639907282f2f709390ad4338eb7f669d43)), closes [EX-3878](https://searchbroker.atlassian.net/browse/EX-3878)
* **desing-system:** Add layout `layout-stack` util. (#1076) ([38db5b3](https://github.com/empathyco/x/commit/38db5b3b4c10a2bd288e9e79b15232f063002156)), closes [EX-8000](https://searchbroker.atlassian.net/browse/EX-8000)
* **desing-system:** Add new color tokens. (#275) ([e93fcc4](https://github.com/empathyco/x/commit/e93fcc4cea0e975441695f14a66b0863cb5896af)), closes [EX-5171](https://searchbroker.atlassian.net/browse/EX-5171)
* **desing-system:** fix the issue with the x-tag and x-filter in the selected filters ([84dfe4b](https://github.com/empathyco/x/commit/84dfe4bd96a768d44f64146b8a45e774450061e2)), closes [EX-4178](https://searchbroker.atlassian.net/browse/EX-4178)
* **device:** Add `device` module ([f21cc69](https://github.com/empathyco/x/commit/f21cc693955ac8f25344cb0e16376fa0eba01e8b)), closes [EX-4243](https://searchbroker.atlassian.net/browse/EX-4243)
* **device:** add `DeviceDetector` component ([07e6b46](https://github.com/empathyco/x/commit/07e6b46bcbd8c3147505ce088224fc75eab5a509)), closes [EX-4244](https://searchbroker.atlassian.net/browse/EX-4244)
* **directives:** add `InfiniteScroll` directive ([37a47a6](https://github.com/empathyco/x/commit/37a47a68f3a063d7bf2d894eb15fabf0abc31779)), closes [EX-3352](https://searchbroker.atlassian.net/browse/EX-3352)
* disable `@typescript-eslint/no-extra-parens` rule (#715) ([3718017](https://github.com/empathyco/x/commit/3718017c5528156f931bc8b1f2d208cdb50781ed)), closes [EX-6996](https://searchbroker.atlassian.net/browse/EX-6996)
* **display-emitter:** support Vue3 to the component (#1555) ([21bcd52](https://github.com/empathyco/x/commit/21bcd5228bf2cc3e8f31d49fe55683788438e089))
* **docs:** add static md file to be copied to docs folder on build proccess ([b40665e](https://github.com/empathyco/x/commit/b40665ee11ffb89311060d12d747de84a16df486)), closes [EX-1943](https://searchbroker.atlassian.net/browse/EX-1943)
* **docs:** Docusaurus integration ([209d47c](https://github.com/empathyco/x/commit/209d47cbcc00597deefff5a69fdc1a4d65e0b58b)), closes [EX-1869](https://searchbroker.atlassian.net/browse/EX-1869)
* e2e test for base result image ([dd16451](https://github.com/empathyco/x/commit/dd16451d8b5ecd3b7682caa83338c7446b0f5070)), closes [EX-3234](https://searchbroker.atlassian.net/browse/EX-3234)
* **e2e test for recommendations components:** e2e test for recommendations component ([0be567f](https://github.com/empathyco/x/commit/0be567f7054cc36185a09d3bab6bf737e92ead96)), closes [EX-3003](https://searchbroker.atlassian.net/browse/EX-3003)
* **e2e testing for query-suggestions component:** e2e testing for query-suggestions component ([589bfe3](https://github.com/empathyco/x/commit/589bfe33eb405be7778c9f06a52c35e426a81f2d)), closes [EX-2912](https://searchbroker.atlassian.net/browse/EX-2912)
* **e2e:** mock adapter for query suggestions tests  ([8566a82](https://github.com/empathyco/x/commit/8566a82954f12bf1592e398a8eed5871596b6f2a)), closes [EX-4645](https://searchbroker.atlassian.net/browse/EX-4645)
* Emit SearchResponseProvided event from Search Module (#864) ([586899d](https://github.com/empathyco/x/commit/586899dbb556f50772bdfd1dc4eb5216ebd15e41)), closes [EX-5167](https://searchbroker.atlassian.net/browse/EX-5167)
* **emitters:** add `isDifferent` optional option to emitters for checking if the observed value has really changed ([d053696](https://github.com/empathyco/x/commit/d0536961bc5afce7259556adbfb9a9c292c0c4f1)), closes [EX-1990](https://searchbroker.atlassian.net/browse/EX-1990)
* EMP-3849 Create vue3-migration-test package ([399fe51](https://github.com/empathyco/x/commit/399fe5176b8c0a5206ed7da4edf9c54c1219f70b))
* **empathize:** add empathize component ([a04c7ad](https://github.com/empathyco/x/commit/a04c7ad2bc59cc065bd76b52f488bef3e3032c7a)), closes [EX-1894](https://searchbroker.atlassian.net/browse/EX-1894)
* **empathize:** add isOpen to store state and expose through the Alias API ([f41905a](https://github.com/empathyco/x/commit/f41905a5d0d6c17e1625a0cfbd9b1bce3c82e940)), closes [EX-4164](https://searchbroker.atlassian.net/browse/EX-4164)
* **empathize:** create empty Empathize module ([1a284fb](https://github.com/empathyco/x/commit/1a284fb5c2e8a0e39710b61c624da31ca709832b)), closes [EX-1804](https://searchbroker.atlassian.net/browse/EX-1804)
* **empathize:** keep Empathize open when focus inside ([395de88](https://github.com/empathyco/x/commit/395de88f6142209366731dbecb8d5a1e507310c5)), closes [EX-2123](https://searchbroker.atlassian.net/browse/EX-2123)
* **empathize:** keyboardNavigation component which deals with arrow keys pressed inside it ([583ec4e](https://github.com/empathyco/x/commit/583ec4ecd0dd2c206798d5b67310327125cc2827)), closes [EX-1804](https://searchbroker.atlassian.net/browse/EX-1804)
* **empathize:** migrate empathize component to composition API (#1481) ([ae34083](https://github.com/empathyco/x/commit/ae34083978ea658f7b740f7a4f701b3dd74c0b2f))
* **empathize:** show Empathize only when it has content  (#820) ([c926335](https://github.com/empathyco/x/commit/c926335a33dca2e8d379accd065726e02bd6f384)), closes [EX-7169](https://searchbroker.atlassian.net/browse/EX-7169)
* **eslint:** add `vuejs-accessibility` plugin (#427) ([6789771](https://github.com/empathyco/x/commit/6789771ab88a909552da74095694a4c2a191a51d)), closes [EX-5845](https://searchbroker.atlassian.net/browse/EX-5845)
* **eslint:** configured ESLint by subfolder and cypress rules ([7919a1b](https://github.com/empathyco/x/commit/7919a1bdef52da6b857ce2264cc18f773fed3e35)), closes [EX-1675](https://searchbroker.atlassian.net/browse/EX-1675)
* **eslint:** update eslint-plugin-x to 1.2.0 version which includes 2.1.2 prettier version ([4569b7e](https://github.com/empathyco/x/commit/4569b7e91df17cef9355664ba342ac29c8c08d45)), closes [EX-2238](https://searchbroker.atlassian.net/browse/EX-2238)
* **eslint:** update version @empathy/eslint-plugin-x to 1.2.1 and fix some files ([acb3ceb](https://github.com/empathyco/x/commit/acb3ceb777496d44ce7d36cb6ab6c7b12f514e5a)), closes [EX-2779](https://searchbroker.atlassian.net/browse/EX-2779)
* **event-button:** add metadata target property to emitted events ([ab83222](https://github.com/empathyco/x/commit/ab83222f08c0768ff652457ba27ad06cefb4ec05)), closes [EX-1663](https://searchbroker.atlassian.net/browse/EX-1663)
* **event-metadata:** add metadata parameter ([0f83b13](https://github.com/empathyco/x/commit/0f83b139ff53fad26e769457bb76c0ebbbae8370)), closes [EX-1617](https://searchbroker.atlassian.net/browse/EX-1617)
* **eventbutton:** add EventButton reusable component ([8e5608c](https://github.com/empathyco/x/commit/8e5608c5bc824b9a9a6d39ee6be0ae8eafbc00a7)), closes [EX-1680](https://searchbroker.atlassian.net/browse/EX-1680)
* **EX-3539:** track PDP add to cart (#306) ([dcad4f6](https://github.com/empathyco/x/commit/dcad4f69ce6b267960f882b3831459e372086272)), closes [EX-3539](https://searchbroker.atlassian.net/browse/EX-3539) [EX-3538](https://searchbroker.atlassian.net/browse/EX-3538)
* **experience-controls:** experience controls module and adapter (#1307) ([6ae3f6b](https://github.com/empathyco/x/commit/6ae3f6b3d537910781dbfebf3b2e670eff391911))
* export pageLoaderButton component (#1449) ([115f744](https://github.com/empathyco/x/commit/115f7448fc92cee5be4151191d4b1a347fd570a1))
* export sticky modifier (#1151) ([8bbd1ab](https://github.com/empathyco/x/commit/8bbd1ab6b0b595c94386bdc0f37d7061df072127))
* export store utils ([663f952](https://github.com/empathyco/x/commit/663f95227815fe2f7a9fcbb0b290774f26b4d7eb)), closes [EX-4742](https://searchbroker.atlassian.net/browse/EX-4742)
* **extra-params:** add new renderless extra params component ([ec844c3](https://github.com/empathyco/x/commit/ec844c359c3d5a7f8ecd389d0138c6c53c839c87)), closes [EX-4605](https://searchbroker.atlassian.net/browse/EX-4605)
* **extra-params:** add new snippet extra params component ([33e68df](https://github.com/empathyco/x/commit/33e68dfdef7e44e67f7e9f4ff093ade235f0c563)), closes [EX-4545](https://searchbroker.atlassian.net/browse/EX-4545)
* **extra-params:** add option to add more extra params using a prop in `SnippetConfigExtraParams` component ([7f9f8b2](https://github.com/empathyco/x/commit/7f9f8b2a7d2a78ed5a101f6e005fffa4f20d3594)), closes [EX-5205](https://searchbroker.atlassian.net/browse/EX-5205)
* **extra-params:** Add support to `UrlHandler` for handling `extra-params` ([4788be1](https://github.com/empathyco/x/commit/4788be15c5c47525279d3fedc3e468aebb1e8610)), closes [EX-4564](https://searchbroker.atlassian.net/browse/EX-4564)
* **extra-params:** allow currency to be an extra param as default ([319851d](https://github.com/empathyco/x/commit/319851da07f04a79aae128081c9c45cd7ae1b1e9))
* **extra-params:** makes `excludedExtraParams` configurable ([ca2bed1](https://github.com/empathyco/x/commit/ca2bed17c7ef8ed893a65e7d1a055901491ea8fa))
* **extra-params:** migrate extra params and snippet config extra params (#1531) ([d869f18](https://github.com/empathyco/x/commit/d869f1886c11f74af8a6350033d7567385ad629d))
* extract SessionService to x-utils package ([5268808](https://github.com/empathyco/x/commit/52688087e577dfd7ce9b0669b21ada75ae67053c))
* **extraParams:** add new extra params module ([f20323d](https://github.com/empathyco/x/commit/f20323d5ae817576b468c04a240eee380e8ff5be)), closes [EX-4585](https://searchbroker.atlassian.net/browse/EX-4585)
* **facets-empty-module:** create empty module for facets ([96631fb](https://github.com/empathyco/x/commit/96631fb08332d9e27bad13253007a85548a1ef20)), closes [EX-2221](https://searchbroker.atlassian.net/browse/EX-2221)
* **facets-module:** Create wire which emits a commit to set the facets in the state ([5cc5a91](https://github.com/empathyco/x/commit/5cc5a9144252b56802fe2c3237a01e2a625109f0)), closes [EX-2222](https://searchbroker.atlassian.net/browse/EX-2222)
* **facets-next:** add `AllFilter`, `BaseFilter` and `EditableNumberRangeFilter` components to `facets-next` x-module. ([8483937](https://github.com/empathyco/x/commit/84839377076cdf97a765d44511b12f770bd9b33f)), closes [EX-4592](https://searchbroker.atlassian.net/browse/EX-4592)
* **facets-next:** add `EditableNumberRangeFilterEntity` ([876da46](https://github.com/empathyco/x/commit/876da466da986de89b40dcceb4119cac816228d1)), closes [EX-4356](https://searchbroker.atlassian.net/browse/EX-4356)
* **facets-next:** add `Facets` component to `facets-next` x-module ([1a4daea](https://github.com/empathyco/x/commit/1a4daeaf6e49dee7c41c0a98811853c32c22e01b)), closes [EX-3661](https://searchbroker.atlassian.net/browse/EX-3661)
* **facets-next:** add `FacetsProvider` component ([c52d972](https://github.com/empathyco/x/commit/c52d972e2d3470e7ae6b159e72b4deeac3971053)), closes [EX-4588](https://searchbroker.atlassian.net/browse/EX-4588)
* **facets-next:** Add `FacetsService` ([3b2871f](https://github.com/empathyco/x/commit/3b2871f9993b8cde206585e863f7c10cbe1f80d9)), closes [EX-3653](https://searchbroker.atlassian.net/browse/EX-3653)
* **facets-next:** add `HierarchicalFilterEntity` (#75) ([d633721](https://github.com/empathyco/x/commit/d633721b6c795ee9145925d366216edd616b0807)), closes [EX-4354](https://searchbroker.atlassian.net/browse/EX-4354)
* **facets-next:** add `RawFilterEntity` ([f87d873](https://github.com/empathyco/x/commit/f87d8737d8a2049f7311294f7c260b36f542014b)), closes [EX-4358](https://searchbroker.atlassian.net/browse/EX-4358)
* **facets-next:** add `SimpleFilter`, `HierarchicalFilter`, `NumberRangeFilter`, `RenderlessFilter` and `Filters` components to the `facets-next` x-module. ([8f82d12](https://github.com/empathyco/x/commit/8f82d123c8dee6dcc403a46684c4793596d44008)), closes [EX-4614](https://searchbroker.atlassian.net/browse/EX-4614)
* **facets-next:** add `SimpleFilterEntity` ([9b551a4](https://github.com/empathyco/x/commit/9b551a41d6e67c64942cfe26051a06ce7dc91a65)), closes [EX-4352](https://searchbroker.atlassian.net/browse/EX-4352)
* **facets-next:** add all remaining components to Facets Next X-Module ([b9e0afc](https://github.com/empathyco/x/commit/b9e0afcbc657ec4925054bcb24f61de5f35fc741)), closes [EX-4615](https://searchbroker.atlassian.net/browse/EX-4615)
* **facets-next:** add entity filter modifiers (#81) ([7074938](https://github.com/empathyco/x/commit/70749382e0a310736ce9b75c5ac1d4466384d0fe)), closes [EX-3651](https://searchbroker.atlassian.net/browse/EX-3651)
* **facets-next:** add facets to the state and facets getter ([27ce68d](https://github.com/empathyco/x/commit/27ce68d47a6414457cd648f261b50bb88e171718)), closes [EX-4584](https://searchbroker.atlassian.net/browse/EX-4584)
* **facets-next:** add module (#64) ([b002637](https://github.com/empathyco/x/commit/b002637c535d9a1654a264cd3c759fc013cf8fdc)), closes [EX-3647](https://searchbroker.atlassian.net/browse/EX-3647)
* **facets-next:** add support for the new search types in search adapter ([aec475e](https://github.com/empathyco/x/commit/aec475e4f689e63a4dc1b0fed3c3ade73b5122f2)), closes [EX-3640](https://searchbroker.atlassian.net/browse/EX-3640)
* **facets-next:** add wiring. add new `wireService` and `wireServiceWithoutPayload` wires factories. ([b28a221](https://github.com/empathyco/x/commit/b28a221b8a23ca2d307f75b01242ccabb7d218e0)), closes [EX-3657](https://searchbroker.atlassian.net/browse/EX-3657)
* **facets-next:** move HierarchicalFilter component to new `facets-next` x-module ([a8c18ea](https://github.com/empathyco/x/commit/a8c18ea47df4ee451a13a55d5e9ee58dc8a5cf56)), closes [EX-4622](https://searchbroker.atlassian.net/browse/EX-4622)
* **facets:** add `click:show-more` & `click:show-less` events to the `SlicedFilters` component. ([133d062](https://github.com/empathyco/x/commit/133d06256e61b7749866e165b647f68f9dba60fc)), closes [EX-4284](https://searchbroker.atlassian.net/browse/EX-4284)
* **facets:** add `ExcludeFiltersWithNoResults` component ([65f271a](https://github.com/empathyco/x/commit/65f271ada42ea1e71620019fb072adb77cfb9769)), closes [EX-3412](https://searchbroker.atlassian.net/browse/EX-3412)
* **facets:** add `isSelected` binding to the All Filter component slot ([50ea508](https://github.com/empathyco/x/commit/50ea508f3caa3d87e02881cd5791c7ebfe65416c)), closes [EX-4173](https://searchbroker.atlassian.net/browse/EX-4173)
* **facets:** add `MultiSelectFilters` component. ([69fbe27](https://github.com/empathyco/x/commit/69fbe275dd32f3e6d6958251495b1c1bdb364785)), closes [EX-2580](https://searchbroker.atlassian.net/browse/EX-2580)
* **facets:** add `PreselectedFilters` component ([5496d78](https://github.com/empathyco/x/commit/5496d7868c77d8b9211fd532bf964770da1d6a3c)), closes [EX-6023](https://searchbroker.atlassian.net/browse/EX-6023)
* **facets:** add `registerModifierByFilterModelName` ([36956a1](https://github.com/empathyco/x/commit/36956a13b33cc5430381d33ac53cd33b706136da)), closes [EX-6106](https://searchbroker.atlassian.net/browse/EX-6106)
* **facets:** add `toggleHierarchicalFilter` action ([bda3d3f](https://github.com/empathyco/x/commit/bda3d3fe2b259228b4ede91dcb768936df9f9c8c)), closes [EX-2459](https://searchbroker.atlassian.net/browse/EX-2459)
* **facets:** add an option to set the state facets via prop ([986d214](https://github.com/empathyco/x/commit/986d21481e2ef2a866906a79e6f243d13e62970f)), closes [EX-2870](https://searchbroker.atlassian.net/browse/EX-2870)
* **facets:** add EditableNumberRangeFilter component ([b8694c1](https://github.com/empathyco/x/commit/b8694c116d1efced74d9c69d9b4249b740ca1042)), closes [EX-3257](https://searchbroker.atlassian.net/browse/EX-3257)
* **facets:** add facets mixin to share logic between components ([c8a9046](https://github.com/empathyco/x/commit/c8a904612213cd12040dd6fa1348f6c9a7726eda)), closes [EX-2899](https://searchbroker.atlassian.net/browse/EX-2899)
* **facets:** add new events for clear filters ([5d2f1a3](https://github.com/empathyco/x/commit/5d2f1a33ceecb4168569db0d4b689d26d7944770)), closes [EX-2561](https://searchbroker.atlassian.net/browse/EX-2561)
* **facets:** add new events, wiring, and action to keep backend filters selected state ([a371917](https://github.com/empathyco/x/commit/a3719171b33f1deb0e9a31148d057a4b88cc3b2c)), closes [EX-3585](https://searchbroker.atlassian.net/browse/EX-3585)
* **facets:** add new filter to deselect the filters if the query has changed ([ebd1b73](https://github.com/empathyco/x/commit/ebd1b73c1ba9979bac6f0ee4424d7b48a73578bb)), closes [EX-3101](https://searchbroker.atlassian.net/browse/EX-3101)
* **facets:** add renderableFacets prop to Facets component to filter rendered facets ([57fe9ca](https://github.com/empathyco/x/commit/57fe9ca50bf69b7939b46774333da490efac3360)), closes [EX-3037](https://searchbroker.atlassian.net/browse/EX-3037)
* **facets:** add Renderless Filter component ([5cc35ab](https://github.com/empathyco/x/commit/5cc35ab02d9ffa85ca33cda9dc94e431b2887f2e)), closes [EX-3608](https://searchbroker.atlassian.net/browse/EX-3608)
* **facets:** add selectedFilters to custom facet and default slots for each facet in facets.vue ([5e71bbf](https://github.com/empathyco/x/commit/5e71bbf0ef0537d81148b1b342b1c6f42f0af913)), closes [EX-2887](https://searchbroker.atlassian.net/browse/EX-2887)
* **facets:** add SelectedFiltersChanged emitter. ([9848b52](https://github.com/empathyco/x/commit/9848b52bbddd138531e37a36570aa1c814110cd7))
* **facets:** Add slot by Facet ModelName. (#572) ([899515a](https://github.com/empathyco/x/commit/899515a1424bfab9a8d937a1feb9507917173807)), closes [EX-6433](https://searchbroker.atlassian.net/browse/EX-6433)
* **facets:** add SortedFilters component ([681969a](https://github.com/empathyco/x/commit/681969a1d073e92d98e0e6e6a37704779f3d5c76))
* **facets:** add support for optional hierarchical filter children prop ([74f81e0](https://github.com/empathyco/x/commit/74f81e0eb94c62199b0ef7046dc9b4e0982ea4fd))
* **facets:** add the option to init the `frontendFacets` via prop in the `Facets` component ([3888c35](https://github.com/empathyco/x/commit/3888c35816b028c76a8d4135d57c9a7ab4196b1e))
* **facets:** add toggleSimpleFilter action ([787cc78](https://github.com/empathyco/x/commit/787cc7808e768acefa5749e0cd335654024d196b)), closes [EX-2458](https://searchbroker.atlassian.net/browse/EX-2458)
* **facets:** add wiring and store logic in facets module to support `EditableNumberRangeFilter` ([c83086c](https://github.com/empathyco/x/commit/c83086c84883b8c8410b208dd454320e72fc5d0e)), closes [EX-3258](https://searchbroker.atlassian.net/browse/EX-3258)
* **facets:** added clearSelectedFilters wire on UserAcceptedAQuery ([6db0c2a](https://github.com/empathyco/x/commit/6db0c2a657226936877fd549f3a4421a25698f17)), closes [EX-2927](https://searchbroker.atlassian.net/browse/EX-2927)
* **facets:** all filter button which deselects its filters ([9538834](https://github.com/empathyco/x/commit/953883436a500845358a73ec9c1dee4c6c90ba4e)), closes [EX-2701](https://searchbroker.atlassian.net/browse/EX-2701)
* **facets:** change `BaseFilter` to `RenderlessFilter` in `HierarchicalFilter` component ([91389dd](https://github.com/empathyco/x/commit/91389ddd291dbce025b72dac8802d4a4180bbbd4)), closes [EX-3590](https://searchbroker.atlassian.net/browse/EX-3590)
* **facets:** change `NumberRangeFilter` component to use `RenderlessFilter` instead of `BaseFilter` ([f0edfac](https://github.com/empathyco/x/commit/f0edfac14a184ed7fefd27e1c1e700848ada4471)), closes [EX-3953](https://searchbroker.atlassian.net/browse/EX-3953)
* **facets:** expose `clickEvents` as a `prop` in filters components using a `RenderlessFilter` ([013d83d](https://github.com/empathyco/x/commit/013d83d93ac734a1365bbf98a19ae15dc2f1a64b)), closes [EX-5986](https://searchbroker.atlassian.net/browse/EX-5986)
* **facets:** extract `base-filter` component from `base-hierarchical-filter` and `base-simple-filter` components. ([c6559a4](https://github.com/empathyco/x/commit/c6559a4d980ae2193b5f640890e60c621a34ed87)), closes [EX-2603](https://searchbroker.atlassian.net/browse/EX-2603)
* **facets:** facets component ([5bb6ea6](https://github.com/empathyco/x/commit/5bb6ea6a75fc4d9a72c30dc7c17dd76287d3e0b6)), closes [EX-2417](https://searchbroker.atlassian.net/browse/EX-2417)
* **facets:** facets split in backend and frontend facets ([f779107](https://github.com/empathyco/x/commit/f779107f9261d47ee8ececb00aeb3db4d8d64f65)), closes [EX-3255](https://searchbroker.atlassian.net/browse/EX-3255)
* **facets:** implement a strategy to decide what filters are sent in the request (#1124) ([a2174b5](https://github.com/empathyco/x/commit/a2174b58d356cc16177cf3d4c2ac3866dadd86b7)), closes [EX-7550](https://searchbroker.atlassian.net/browse/EX-7550)
* **facets:** keep selection state of the current filters ([8cf2b63](https://github.com/empathyco/x/commit/8cf2b63778ce50a454aa4f3574761609918a3695)), closes [EX-2654](https://searchbroker.atlassian.net/browse/EX-2654)
* **facets:** make `SimpleFilter` component use `RenderlessFilter`, exposing the option of changing the default button. ([6a0633e](https://github.com/empathyco/x/commit/6a0633e311b98c52003b562109d839fb3b6d2309)), closes [EX-3589](https://searchbroker.atlassian.net/browse/EX-3589)
* **facets:** migrate AllFilter component to Composition API (#1535) ([0b00671](https://github.com/empathyco/x/commit/0b006711297f6fb3721622082fe63b87ce4bcbf7))
* **facets:** Move filters flattening from `x-adapter-platform` to `x-components`. (#626) ([2bebaeb](https://github.com/empathyco/x/commit/2bebaeb2863fe794f1b3bea924904651b9302ef6)), closes [EX-6484](https://searchbroker.atlassian.net/browse/EX-6484)
* **facets:** remove filters on new query (#717) ([e452ece](https://github.com/empathyco/x/commit/e452ecebb194b2fa248402405e26ed1044c1d849)), closes [EX-6196](https://searchbroker.atlassian.net/browse/EX-6196)
* **facets:** remove old `facets` X Module and replace by `facets-next`. ([a47d99f](https://github.com/empathyco/x/commit/a47d99fd9ccbb046c5a5054a92e723f2675b7563)), closes [EX-3663](https://searchbroker.atlassian.net/browse/EX-3663)
* **facets:** selected filters component which renders selected filters ([11c9e43](https://github.com/empathyco/x/commit/11c9e43b02df785baa72de55177c0d61fe270a4a)), closes [EX-2855](https://searchbroker.atlassian.net/browse/EX-2855)
* **facets:** support receiving facets containing selected filters in `Facets.vue` ([9ee7080](https://github.com/empathyco/x/commit/9ee70805659e5296152a00dbde429db5f02eab9d)), closes [EX-3092](https://searchbroker.atlassian.net/browse/EX-3092)
* **facets:** Unify __unknown__ and __unknown-facet__ in a constant (#1351) ([30585f2](https://github.com/empathyco/x/commit/30585f2d57653aa33c68f748ff10f93202f1887e))
* **facets:** update facets module with new search-types ([7f1ec20](https://github.com/empathyco/x/commit/7f1ec20fdf5fbe5a31277b6d95e7dfd2c3a76039)), closes [EX-2509](https://searchbroker.atlassian.net/browse/EX-2509)
* **facets:** update search-types and search-adapter to allow EditableNumberRangeFilters ([d8a62e8](https://github.com/empathyco/x/commit/d8a62e85523d125a9e62ccc6a2052e4a33c1038a)), closes [EX-3367](https://searchbroker.atlassian.net/browse/EX-3367)
* **facets:** use the new decorators `inject` and `provide` in the filters components ([d7030b9](https://github.com/empathyco/x/commit/d7030b91747217d6478c768eea0106830d67a1fd)), closes [EX-3465](https://searchbroker.atlassian.net/browse/EX-3465)
* **fallback-disclaimer:** migration to composition api (#1545) ([6af6737](https://github.com/empathyco/x/commit/6af6737e854616567822e6ea5a09f093a7368960))
* filter query preview (#1296) ([9543c47](https://github.com/empathyco/x/commit/9543c477cd8a305fd89edb9b24d046c774537c9b))
* filters in history queries (#1315) ([1e266d9](https://github.com/empathyco/x/commit/1e266d9ce8dbf5661488800bc9566f117c1616f5))
* **filters:** new filtersMap getter and selectedFilters getter refactor ([21fa50f](https://github.com/empathyco/x/commit/21fa50fd1088641d99c8cab48d275764a4b0e0c8))
* **filters:** renders a selected filters from state and exposes slots to customize it ([d4e0978](https://github.com/empathyco/x/commit/d4e09786a2af5228553c665d58fcf10d67ce3833)), closes [EX-2863](https://searchbroker.atlassian.net/browse/EX-2863)
* **filters:** update preselected filters component so it reacts to snippetConfig changes (#1404) ([05983f3](https://github.com/empathyco/x/commit/05983f352830b7d52c2b586566938749fa9ce44e))
* fix form label warnings ([2437b09](https://github.com/empathyco/x/commit/2437b096ca1ddb9b97c3207e338b9fb587bc3ea7)), closes [EX-6025](https://searchbroker.atlassian.net/browse/EX-6025)
* fix rest of warnings for accessibility ([553d5ba](https://github.com/empathyco/x/commit/553d5bac9256871e69de2c3b87dfc99a993d0f1f)), closes [EX-6149](https://searchbroker.atlassian.net/browse/EX-6149)
* **getters-proxy:** add cache to the getters proxy ([7ed2f05](https://github.com/empathyco/x/commit/7ed2f054204bd9807d97ae304017e7f9ebefc3ca))
* **getters-query-suggestions:** create getters for query suggestions to use property hideIfEqualsQuery ([e19ccba](https://github.com/empathyco/x/commit/e19ccba84c4f15371e4b6c6475b31ec69e681772)), closes [EX-2296](https://searchbroker.atlassian.net/browse/EX-2296)
* **global-config:** add global configuration XConfig ([46aef97](https://github.com/empathyco/x/commit/46aef978257710128716ea40c3292d0e0aee2472)), closes [EX-1604](https://searchbroker.atlassian.net/browse/EX-1604)
* **grid:** add BaseColumnPickerDropdown component ([64b1610](https://github.com/empathyco/x/commit/64b161092a4da843f6ef61ff70c9b5c18185d609)), closes [EX-3296](https://searchbroker.atlassian.net/browse/EX-3296)
* hidde overflow-y in the sliding panel (#768) ([3458e61](https://github.com/empathyco/x/commit/3458e618005e6a1bcd875127749a90b411b80f86)), closes [EX-7015](https://searchbroker.atlassian.net/browse/EX-7015)
* **highlight:** migrate highlight component to composition API (#1486) ([10dd541](https://github.com/empathyco/x/commit/10dd5417f861d6e1152483abbd510059d2917f48))
* history-queries-switch wai aria adjustments (#847) ([c05e194](https://github.com/empathyco/x/commit/c05e194306520aef2d8d684f38f616ab26e9ebf9)), closes [EX-7344](https://searchbroker.atlassian.net/browse/EX-7344)
* **history-queries:** add `HistoryQueriesSwitch` component (#593) ([8c87cc3](https://github.com/empathyco/x/commit/8c87cc3a35336720d3da79ab7347e52caa4cd922)), closes [EX-6515](https://searchbroker.atlassian.net/browse/EX-6515)
* **history-queries:** add `my-history` component ([a7de7f2](https://github.com/empathyco/x/commit/a7de7f297251bf4290787e362f46b2ab3ec6a428)), closes [EX-3582](https://searchbroker.atlassian.net/browse/EX-3582)
* **history-queries:** add `MyHistory` component ([9929212](https://github.com/empathyco/x/commit/992921275edcca7a6c14ab6dfeaa2dbacae6a5e8)), closes [EX-5703](https://searchbroker.atlassian.net/browse/EX-5703)
* **history-queries:** add `UserClickedDismissDisableHistoryQueries` event ([ea0bddc](https://github.com/empathyco/x/commit/ea0bddce87ec1e87b753bb39863cbee903fb9eed)), closes [EX-6682](https://searchbroker.atlassian.net/browse/EX-6682)
* **history-queries:** add actions ([9f2243f](https://github.com/empathyco/x/commit/9f2243f0621bdf9f8e4013657e1c570f0f14a918)), closes [EX-1764](https://searchbroker.atlassian.net/browse/EX-1764)
* **history-queries:** add ClearHistoryQueries Component ([ccb3e96](https://github.com/empathyco/x/commit/ccb3e96c8a9391671e43e1bc86774c97bfe67789)), closes [EX-1763](https://searchbroker.atlassian.net/browse/EX-1763)
* **history-queries:** add delete-history-query component ([73384fd](https://github.com/empathyco/x/commit/73384fdc76217225d0ea6505da78d836be2d5a92)), closes [EX-1778](https://searchbroker.atlassian.net/browse/EX-1778)
* **history-queries:** add DeleteHistoryQuery component ([de082e0](https://github.com/empathyco/x/commit/de082e01f2e88a72d1b49097a86e0e8f1aca373a)), closes [EX-1778](https://searchbroker.atlassian.net/browse/EX-1778)
* **history-queries:** add dynamic classes to the history query suggestion (#1014) ([ddd4ac7](https://github.com/empathyco/x/commit/ddd4ac76f30f90bb68497d507948caee060944cf)), closes [EX-7853](https://searchbroker.atlassian.net/browse/EX-7853)
* **history-queries:** add dynamic classes to the remove history query button (#1007) ([b5623d1](https://github.com/empathyco/x/commit/b5623d1c6f7f2709251164c6055b616218163c6f)), closes [EX-7833](https://searchbroker.atlassian.net/browse/EX-7833)
* **history-queries:** add history queries emitters ([38cb7a8](https://github.com/empathyco/x/commit/38cb7a849c4d94b0796979756dd6a67d0c42081d)), closes [EX-1738](https://searchbroker.atlassian.net/browse/EX-1738)
* **history-queries:** add history queries getters ([35a3814](https://github.com/empathyco/x/commit/35a3814737633e08365621a73072abe5954fa4a3)), closes [EX-1735](https://searchbroker.atlassian.net/browse/EX-1735)
* **history-queries:** add history queries module wiring. ([d598973](https://github.com/empathyco/x/commit/d598973f5bd361332c5f60bbbb33b54b272270b2)), closes [EX-1738](https://searchbroker.atlassian.net/browse/EX-1738)
* **history-queries:** add history queries store for its x-module ([c9f3df2](https://github.com/empathyco/x/commit/c9f3df21f78af89a058e1af2f6080a813fb9e5ed)), closes [EX-1764](https://searchbroker.atlassian.net/browse/EX-1764)
* **history-queries:** add history queries x-module skeleton ([71d21c5](https://github.com/empathyco/x/commit/71d21c5e64095440fdec253549524746a3f16a2b)), closes [EX-1735](https://searchbroker.atlassian.net/browse/EX-1735)
* **history-queries:** add history-queries module to app & its e2e testing ([29bacb5](https://github.com/empathyco/x/commit/29bacb50255ddbe89531389589737e34c5fb51fb)), closes [EX-1762](https://searchbroker.atlassian.net/browse/EX-1762)
* **history-queries:** add HistoryQueries component ([50397f4](https://github.com/empathyco/x/commit/50397f4c45305c1f1bdd3948a4cbd8f12265fc43)), closes [EX-1739](https://searchbroker.atlassian.net/browse/EX-1739)
* **history-queries:** add load history queries action ([a761bce](https://github.com/empathyco/x/commit/a761bce14a0656335f6d52742511fa54a53661f7)), closes [EX-1764](https://searchbroker.atlassian.net/browse/EX-1764)
* **history-queries:** add module events ([2ac5dbf](https://github.com/empathyco/x/commit/2ac5dbf2bb074434ce000a264ebf34986cb45200)), closes [EX-1736](https://searchbroker.atlassian.net/browse/EX-1736)
* **history-queries:** add toggle to enable/disable the history queries ([655b55a](https://github.com/empathyco/x/commit/655b55a3f10788073a842d18f7849634e5f94376)), closes [EX-5600](https://searchbroker.atlassian.net/browse/EX-5600)
* **history-queries:** bind `formatTime` to `suggestion-content` slot (#598) ([589eef2](https://github.com/empathyco/x/commit/589eef287534e9916dcda7b0ad86626eb450decd)), closes [EX-6611](https://searchbroker.atlassian.net/browse/EX-6611)
* **history-queries:** bind formatTime callback to MyHistory suggestion slot (#1049) ([0e20cf3](https://github.com/empathyco/x/commit/0e20cf3315b2f2a687ee63b14bb50bac021eb57f)), closes [EX-7879](https://searchbroker.atlassian.net/browse/EX-7879)
* **history-queries:** disable `MyHistory` without confirmation when the `history queries` list is empty (#615) ([8b0b1d6](https://github.com/empathyco/x/commit/8b0b1d6e818557eba9482dcd149ed3882ca6c854)), closes [EX-6696](https://searchbroker.atlassian.net/browse/EX-6696)
* **history-queries:** emit click event on HistoryQuery click (#1048) ([2e7d074](https://github.com/empathyco/x/commit/2e7d07484571a9458a14fab4435b10523f6e7457)), closes [EX-7879](https://searchbroker.atlassian.net/browse/EX-7879)
* **history-queries:** expose `historyQueriesWithResults` in the alias API (#991) ([90c17f5](https://github.com/empathyco/x/commit/90c17f54a1bc1a4c613d06e64dd630f9e1efca61)), closes [EX-7476](https://searchbroker.atlassian.net/browse/EX-7476)
* **history-queries:** Hide history queries with no results (#865) ([58f155d](https://github.com/empathyco/x/commit/58f155d2eefe1676646d320c9f310ad1d28aab5e))
* **history-queries:** trim query before storing it ([5a77b11](https://github.com/empathyco/x/commit/5a77b11fc7a625f1d9f8dafa1b1b295ecf253add)), closes [EX-1764](https://searchbroker.atlassian.net/browse/EX-1764)
* **history:** modify history-queries to accept new config and show all the elements in store. Tests. ([f99d8ea](https://github.com/empathyco/x/commit/f99d8eaaf16be3af7bb102d0d49d14c01cec20c0)), closes [EX-3389](https://searchbroker.atlassian.net/browse/EX-3389)
* **icons:** migrate icons to composition API (#1551) ([243419f](https://github.com/empathyco/x/commit/243419f15b504cea6f8db3ef53899915a174a031))
* **identifier-results:** add extra params in the x-module ([6afff42](https://github.com/empathyco/x/commit/6afff426081b645bb0e878c77915a4c319b847d2)), closes [EX-5066](https://searchbroker.atlassian.net/browse/EX-5066)
* **identifier-results:** add IdentifierResult component ([118ef1f](https://github.com/empathyco/x/commit/118ef1f359c7fa827d86949f4c04554b025e80ac)), closes [EX-1958](https://searchbroker.atlassian.net/browse/EX-1958)
* **identifier-results:** add maxItemsToRender prop (#576) ([c740b8b](https://github.com/empathyco/x/commit/c740b8b8c1a66d25eb8cc2aaa84303cb186ae8ea)), closes [EX-6414](https://searchbroker.atlassian.net/browse/EX-6414)
* **identifier-results:** add mutations and actions to the module ([aa26692](https://github.com/empathyco/x/commit/aa2669206aa156bfd653e4105db48be196a9f763)), closes [EX-1942](https://searchbroker.atlassian.net/browse/EX-1942)
* **identifier-results:** add query origin in the identifier results search ([9c75236](https://github.com/empathyco/x/commit/9c75236bd21b0c483e01a62eb42a070510ea3cf2)), closes [EX-4873](https://searchbroker.atlassian.net/browse/EX-4873)
* **identifier-results:** create identifier results module with getters ([f2bfb56](https://github.com/empathyco/x/commit/f2bfb5652f4a5ba24dc12c2c1284691f8f6398dc)), closes [EX-1942](https://searchbroker.atlassian.net/browse/EX-1942)
* **identifier-results:** identifierResults component and module wiring ([c94ebfb](https://github.com/empathyco/x/commit/c94ebfb51015f1a8f9ba1bc58150ee665bc59f24)), closes [EX-1957](https://searchbroker.atlassian.net/browse/EX-1957)
* **immediate-store-emitters:** add immediate option for store emitters configuration ([8aadd94](https://github.com/empathyco/x/commit/8aadd943132f30aac1f2cdc6bdc754fb357a693e)), closes [EX-1642](https://searchbroker.atlassian.net/browse/EX-1642)
* Improve `tailwindcss` types (#730) ([b7ab20c](https://github.com/empathyco/x/commit/b7ab20cfb0faa7f21fdf4aaaa4ae3e6d44bc6a79)), closes [EX-7041](https://searchbroker.atlassian.net/browse/EX-7041)
* improve customization and add prop classes to editable-number-range-filter (#1253) ([fda4cc6](https://github.com/empathyco/x/commit/fda4cc69be19399647ba1128ebb872b8eb36e011))
* Improve tailwindcss types. (#725) ([14dec97](https://github.com/empathyco/x/commit/14dec974174cd18e63cb5f4e9a690a9989de44bc)), closes [EX-6790](https://searchbroker.atlassian.net/browse/EX-6790)
* **keyboard-navigation:** add SpatialNavigation service to use in keyboard navigation component ([521dd32](https://github.com/empathyco/x/commit/521dd32056b53246c13b908b016b66f2bf332512)), closes [EX-1924](https://searchbroker.atlassian.net/browse/EX-1924)
* **keyboard-navigation:** migrate keyboard-navigation component to composition API (#1493) ([4cf31c9](https://github.com/empathyco/x/commit/4cf31c9df4b751514deaaef4c9abfe4ee5ddfc40))
* **linter:** add x eslint plugin ([34381e5](https://github.com/empathyco/x/commit/34381e537dc03d474a26bef39d6f82dd6cd85fb7)), closes [EX-1946](https://searchbroker.atlassian.net/browse/EX-1946)
* **main-modal:** make events configurable via props (#1590) ([60d630c](https://github.com/empathyco/x/commit/60d630ca2a181d2919b9f1019abbf1eee5dd2c30))
* make `adapter` configurable in the `home` view (#750) ([0fcc5cf](https://github.com/empathyco/x/commit/0fcc5cf38995a439b3011e1b7d94e7edaa7f9ce5)), closes [EX-7073](https://searchbroker.atlassian.net/browse/EX-7073)
* make `XAPI` init method async (#1228) ([9d7d323](https://github.com/empathyco/x/commit/9d7d3230610761be23ca9efd117e7e3c4b9586b5))
* make base dropdown based components accesible (#846) ([71d4233](https://github.com/empathyco/x/commit/71d4233ad5c18fb19f205591bf8b9a0adf160884))
* make internal demo app functional (#1574) ([a485dea](https://github.com/empathyco/x/commit/a485dea768918280e2fec46cae0d5a3f4932002f))
* make the snippet-config-extra-params component react to prop changes ([9f73735](https://github.com/empathyco/x/commit/9f737351324f2fdff044f7e6b6da8a38216b4ab9))
* migrate `Banner` and `Promoted` to composition API (#1506) ([c102fd9](https://github.com/empathyco/x/commit/c102fd96b26425df2ed8d73d58b3db8fc454deeb))
* migrate `facets provider` component to use Composition API (#1523) ([eff7b8d](https://github.com/empathyco/x/commit/eff7b8d92c54aece07061c2d8ce58507a56e7d01))
* migrate `FiltersInjection` mixin (#1467) ([839c663](https://github.com/empathyco/x/commit/839c66334c98ed399ce354a2c5a3a842734ed54c))
* migrate `identifier-results` x-module to composition API (#1521) ([81b18d0](https://github.com/empathyco/x/commit/81b18d03b3ae2ba9df05f5c288a7eab0e0e7966c))
* migrate `ItemsListInjection` mixin (#1460) ([a89fb51](https://github.com/empathyco/x/commit/a89fb5179de040695f13d56f43de50917e1c7f97))
* migrate `MainScroll` and `MainScrollItem` components (#1456) ([b720132](https://github.com/empathyco/x/commit/b7201322bbf1f5696e80e00622d21d653228177c))
* migrate `next-queries` module to composition API ([324d5d8](https://github.com/empathyco/x/commit/324d5d866167352b9ad5e1b2858853ce197fe7fe))
* migrate `query suggestions` module to composition api (#1497) ([4a9c742](https://github.com/empathyco/x/commit/4a9c742007476367328be6c978d16ec16ae115c1))
* migrate `QueryPreviewButton` component to composition API (#1525) ([3eff0c7](https://github.com/empathyco/x/commit/3eff0c7c9479abbebbda59e8cc538af6f55375e1))
* migrate `Redirection` component to composition api (#1532) ([93c0809](https://github.com/empathyco/x/commit/93c08094a33f9828631ad4e4bbb9ac7831db5963))
* migrate `Spellcheck` and `SpellcheckButton` components to composition api (#1518) ([0e848a7](https://github.com/empathyco/x/commit/0e848a70d69a780b4a053d5bc78b432178f21327))
* migrate base suggestions component to composition API ([34bd833](https://github.com/empathyco/x/commit/34bd833e58f9b5f559df17ec2781e529476cdda8))
* migrate base-grid component to vue 2.7 (#1441) ([1974715](https://github.com/empathyco/x/commit/19747154d727bec6cbee171df7d655c34f714db0))
* migrate base-switch to use defineComponent sintax (#1415) ([0592ec9](https://github.com/empathyco/x/commit/0592ec94f7f47c91946d0e3a465dde134dd12021))
* migrate BaseEventsModal to composition API ([7ef04b6](https://github.com/empathyco/x/commit/7ef04b65bcef2eb9b9dc5bc107bc02823831d444))
* migrate device-detector component (#1544) ([4083571](https://github.com/empathyco/x/commit/4083571bd2fdfc268b529c4ea5a02acb81eecc32))
* migrate experience controls (#1530) ([91ee6d0](https://github.com/empathyco/x/commit/91ee6d0f171b870c42e6dcc95229a6be66b7067e))
* migrate filters components to Composition API (#1550) ([dd6a2d7](https://github.com/empathyco/x/commit/dd6a2d728632e81c25cc918c1cac1aa10daab590))
* migrate filters to vue 3 syntax (#1144) ([6413883](https://github.com/empathyco/x/commit/641388380620ab0d66cea627244912b6f3b2210d))
* migrate from `vue-cli` to `vite` (#1350) ([52a3b6e](https://github.com/empathyco/x/commit/52a3b6e7d94587f6934e838a2e68c99af97f7999))
* migrate history queries x module to composition api (#1494) ([cd51e9b](https://github.com/empathyco/x/commit/cd51e9bb2afb77bbb8f935445bfda360dcfaafde))
* migrate internal view components (#1563) ([df0d026](https://github.com/empathyco/x/commit/df0d02634d1193f35918a5c8fd6913faa65c9ab7))
* migrate modals to vue 3 syntax (#1141) ([d04b522](https://github.com/empathyco/x/commit/d04b522607787bdfe887896a26895d00fdd0d369))
* migrate panels components to vue 3 syntax (#1150) ([5ef137c](https://github.com/empathyco/x/commit/5ef137cbf84d5f68a611a5ecb51cb8454c0a7422))
* migrate PartialQueryButton and PartialResultsList (#1501) ([5e87123](https://github.com/empathyco/x/commit/5e87123d4a6c1edeb05f83c31ee8f096b5558e0f))
* migrate popular-searches x-module (#1524) ([f79456d](https://github.com/empathyco/x/commit/f79456d4589b3f9dee5fd86fad9625b853dde267))
* migrate result variant provider (#1440) ([b981d9b](https://github.com/empathyco/x/commit/b981d9ba35394288957e13adbffbaaded142e6c7))
* migrate result variants selector component (#1438) ([1e6d681](https://github.com/empathyco/x/commit/1e6d681d7368ca04810df5d8d6116e702face4ff))
* migrate results to vue 3 syntax (#1145) ([820622a](https://github.com/empathyco/x/commit/820622ab6a37d03de1e4843df2bdbb9daea57e58))
* migrate RTs module to composition API (#1498) ([22c5325](https://github.com/empathyco/x/commit/22c5325666441121e8ee64bfaa4c51ddad11939a))
* migrate Scroll and ScrolToTop componentes (#1562) ([c8182f4](https://github.com/empathyco/x/commit/c8182f4a4435e1e62e7eaee518fb6325fe01bf7e))
* migrate semantics queries module to composition api (#1508) ([72914a2](https://github.com/empathyco/x/commit/72914a25195e2e546da343d32c6a4544b38bdd91))
* migrate suggestions and currency components to vue 3 syntax (#1159) ([67beb82](https://github.com/empathyco/x/commit/67beb820722521e0db3cfdc9ae039e52e6d268f7))
* migrate url-handler x-module (#1556) ([9445758](https://github.com/empathyco/x/commit/94457580884be4b03ec72fa18231350bdf3f115a))
* migrating base-rating component using defineComponent sintax (#1419) ([3fb116a](https://github.com/empathyco/x/commit/3fb116ad5a28addcf53c6d66035072e7013a7818))
* Minor improvements. (#1109) ([1c9dace](https://github.com/empathyco/x/commit/1c9dacea7c46eb0b27687730a8a4978d0e49b230)), closes [EX-8130](https://searchbroker.atlassian.net/browse/EX-8130)
* **mixin:** add origin injection in the mixin and the bus ([2304155](https://github.com/empathyco/x/commit/2304155aa5ab422193e4a9f01755c066a25f0c9e)), closes [EX-4636](https://searchbroker.atlassian.net/browse/EX-4636)
* modify base-events-modal-close and base-events-modal-open for WCAG compliance (#946) ([1f5abdf](https://github.com/empathyco/x/commit/1f5abdf36c6eec18b73f13a78be4c7616016d6fd)), closes [EX-7669](https://searchbroker.atlassian.net/browse/EX-7669)
* modify search function in XAPI to open X (#96) ([9c42da0](https://github.com/empathyco/x/commit/9c42da0af70dfdb5f767eccb08f47e402ac47a70)), closes [EX-3555](https://searchbroker.atlassian.net/browse/EX-3555)
* modify use-$x composable (#1434) ([cd9a0d1](https://github.com/empathyco/x/commit/cd9a0d1acc95e9b79142aa1abe4b5df5d04aef40))
* move `Request` types to `x-types` package ([7cc85c1](https://github.com/empathyco/x/commit/7cc85c1d371b604b3188d8cc2076eab5fc9460e4)), closes [EX-6066](https://searchbroker.atlassian.net/browse/EX-6066)
* move `response` types to `@empathyco/x-types` ([77fb812](https://github.com/empathyco/x/commit/77fb812b77fe0c84462a4b5b2eb7f0439e2d8061)), closes [EX-6092](https://searchbroker.atlassian.net/browse/EX-6092)
* Move `XAPI` from `window.X` to `window.InterfaceX` (#599) ([4538778](https://github.com/empathyco/x/commit/45387783c947f859667f2786ba9013b83b952063)), closes [EX-6645](https://searchbroker.atlassian.net/browse/EX-6645)
* move related tags concatenation logic (#365) ([4e71797](https://github.com/empathyco/x/commit/4e717970198f67018a9b66ed6e47f511ecef4c62)), closes [EX-5410](https://searchbroker.atlassian.net/browse/EX-5410)
* **next queries:** add maxItemsToRender prop ([6bd8c5e](https://github.com/empathyco/x/commit/6bd8c5eb5cecdfac040335a712d4cc17ed22c90b)), closes [EX-2030](https://searchbroker.atlassian.net/browse/EX-2030)
* **next-queries:** add `concatWhenNoMoreItems` prop (#705) ([ac73fb7](https://github.com/empathyco/x/commit/ac73fb7d2e66c3cb1aab0b64586d9e86495436de)), closes [EX-6841](https://searchbroker.atlassian.net/browse/EX-6841)
* **next-queries:** add `maxItemsToRender` prop to `NextQueryPreview` component (#646) ([848427c](https://github.com/empathyco/x/commit/848427cb9dae85c72549ab026b3785194ec4adbd)), closes [EX-6820](https://searchbroker.atlassian.net/browse/EX-6820)
* **next-queries:** add `NextQueriesList` component. ([eeb66c8](https://github.com/empathyco/x/commit/eeb66c865d9ca269ee4ef54e664c272a2d9ef233)), closes [EX-4527](https://searchbroker.atlassian.net/browse/EX-4527)
* **next-queries:** add `origin` to `next queries preview` (#746) ([8928676](https://github.com/empathyco/x/commit/89286768a007d9b8888bfbc6db43c39b6d963380)), closes [EX-6757](https://searchbroker.atlassian.net/browse/EX-6757)
* **next-queries:** add config for the next queries module ([68148b7](https://github.com/empathyco/x/commit/68148b75cb35d5f7756e9923886366c3f1ca8067)), closes [EX-1731](https://searchbroker.atlassian.net/browse/EX-1731)
* **next-queries:** add events types for the next queries module ([f39fcf5](https://github.com/empathyco/x/commit/f39fcf564bf4068c8b3e72df1bf025db4a8835f8)), closes [EX-1730](https://searchbroker.atlassian.net/browse/EX-1730)
* **next-queries:** add extra params in the request ([d6b362b](https://github.com/empathyco/x/commit/d6b362ba94c1755004f005b6841c03a4e73bfe98)), closes [EX-4624](https://searchbroker.atlassian.net/browse/EX-4624)
* **next-queries:** add isCurated property ([8b7b313](https://github.com/empathyco/x/commit/8b7b3132c7fa8aff095a92c84abdc150be705976)), closes [EX-5152](https://searchbroker.atlassian.net/browse/EX-5152)
* **next-queries:** add Next Queries Component ([ed5d0e8](https://github.com/empathyco/x/commit/ed5d0e826a9c6d7076b1754f0fd6a7d67759e8db)), closes [EX-1734](https://searchbroker.atlassian.net/browse/EX-1734)
* **next-queries:** add next query preview component (#631) ([1513ab1](https://github.com/empathyco/x/commit/1513ab1ef0cbcf42d72f483d99815eba76b5eaad)), closes [EX-6646](https://searchbroker.atlassian.net/browse/EX-6646)
* **next-queries:** add next query preview logic (#611) ([fc611fa](https://github.com/empathyco/x/commit/fc611faa39e63e5f916cd19928e9ab0755f8dc7f)), closes [EX-6119](https://searchbroker.atlassian.net/browse/EX-6119)
* **next-queries:** add next-queries x-module ([ad6dbce](https://github.com/empathyco/x/commit/ad6dbceb25f5d8d12c803753d92e0465a303bbc7)), closes [EX-1627](https://searchbroker.atlassian.net/browse/EX-1627)
* **next-queries:** add NextQueriesChanged emitter to next queries emitters ([270bc81](https://github.com/empathyco/x/commit/270bc8112898318318f90fa8728d4343421d7fde)), closes [EX-1732](https://searchbroker.atlassian.net/browse/EX-1732)
* **next-queries:** add NextQueriesChanged emitter to next queries emitters ([499d7a1](https://github.com/empathyco/x/commit/499d7a129832fe6c4f1d3b2cbb15da4e52c34412)), closes [EX-1732](https://searchbroker.atlassian.net/browse/EX-1732)
* **next-queries:** add the NextQuery component ([837dc12](https://github.com/empathyco/x/commit/837dc12695649f5f10d4719995328349f48f506a)), closes [EX-1733](https://searchbroker.atlassian.net/browse/EX-1733)
* **no-element:** change NoElement component to be not functional ([ba0b3c4](https://github.com/empathyco/x/commit/ba0b3c4967037c2254d2a3e67639ba6c93c4e325)), closes [EX-3997](https://searchbroker.atlassian.net/browse/EX-3997)
* **no-suggestions:** append no-suggestions component ([06361d4](https://github.com/empathyco/x/commit/06361d44e5d335ed7978b2e1282fa09386f504c0)), closes [EX-1741](https://searchbroker.atlassian.net/browse/EX-1741)
* **no-suggestions:** append store, configuration, wiring and skeleton no-suggestions x-module ([457d350](https://github.com/empathyco/x/commit/457d350033360797b5e0a50edad66c92ba53143a)), closes [EX-1741](https://searchbroker.atlassian.net/browse/EX-1741)
* **no-suggestions:** Remove `no-suggestions` module. ([4a859e7](https://github.com/empathyco/x/commit/4a859e787736feccc0a38b25ae7594553f8f4978)), closes [EX-4736](https://searchbroker.atlassian.net/browse/EX-4736)
* **open-button:** add open-button component ([4f078bf](https://github.com/empathyco/x/commit/4f078bf181f7c4e643155f53ccc3088d4cf3998f)), closes [EX-1765](https://searchbroker.atlassian.net/browse/EX-1765)
* **panels:** add new `BaseIdPanelToggleButton` and `BaseIdPanelToggle` components ([c50cc26](https://github.com/empathyco/x/commit/c50cc2654d6ceb731be1f185e7a2540bf6dd20d9)), closes [EX-4100](https://searchbroker.atlassian.net/browse/EX-4100)
* **panels:** migrate `base-panels` components to composition api (#1491) ([077ad4d](https://github.com/empathyco/x/commit/077ad4d1bcc1dcf0ae2e16a02f1ac073481a1892))
* place modal under selected element (#829) ([1f46d42](https://github.com/empathyco/x/commit/1f46d428dccdf4807110afc48b5fd600b41bfeae))
* **platform-adapter:** add semantic queries to platform adapter (#1212) ([82bd567](https://github.com/empathyco/x/commit/82bd56704638b050e323d486c43ebcb8cae1d41d))
* **plugin:** minimise initial duplicated requests using a debounce ([3ad1fd4](https://github.com/empathyco/x/commit/3ad1fd4ec949de1f1484919d0165f9e6eaa3d882)), closes [EX-4718](https://searchbroker.atlassian.net/browse/EX-4718)
* **plugin:** move alias creation from created hook to beforeCreated ([57f98e6](https://github.com/empathyco/x/commit/57f98e6587c0c589c4b6581a5f2c1da1a45757d8)), closes [EX-4331](https://searchbroker.atlassian.net/browse/EX-4331)
* **plugin:** replace old bus implementation using the new `x-priority-bus` (#1086) ([f64f9b6](https://github.com/empathyco/x/commit/f64f9b68225c4ee422eb007784e0eec813c95228)), closes [EX-7283](https://searchbroker.atlassian.net/browse/EX-7283)
* **popular-searches:** add config to popular-searches x-module ([7d5e6e1](https://github.com/empathyco/x/commit/7d5e6e1b362117e0d34a1079c6a6bf99cf6a751f)), closes [EX-1714](https://searchbroker.atlassian.net/browse/EX-1714)
* **popular-searches:** add extra params ([697055e](https://github.com/empathyco/x/commit/697055eb28bf4640eb879d4559d083c51ab775f9)), closes [EX-4623](https://searchbroker.atlassian.net/browse/EX-4623)
* **popular-searches:** add hide popular searches that have already been searched in session ([1818023](https://github.com/empathyco/x/commit/1818023e956aaafcdc918dc1868b32c1ec9d37d9)), closes [EX-2128](https://searchbroker.atlassian.net/browse/EX-2128)
* **popular-searches:** add popular-searches x-module ([deeb7ac](https://github.com/empathyco/x/commit/deeb7ac450de5d7c7dac48011e428c6ebc776196)), closes [EX-1610](https://searchbroker.atlassian.net/browse/EX-1610)
* **popular-searches:** append popular searches x-modules events ([b4a40a2](https://github.com/empathyco/x/commit/b4a40a22ce84070c4da496d879a553f5cae630a2)), closes [EX-1713](https://searchbroker.atlassian.net/browse/EX-1713)
* **popular-searches:** append PopularSearch component ([ba23a25](https://github.com/empathyco/x/commit/ba23a257de87273f91740d0db8c20062f638df3a)), closes [EX-1717](https://searchbroker.atlassian.net/browse/EX-1717)
* **prettier:** add prettier-organize-imports plugin ([3a70ab2](https://github.com/empathyco/x/commit/3a70ab2d18c9f56373f000299d4fcefb6e2f67dc)), closes [EX-1787](https://searchbroker.atlassian.net/browse/EX-1787)
* **pure-suggestion:** add base suggestion to reuse in every suggestion type ([7b2dbc6](https://github.com/empathyco/x/commit/7b2dbc6574376b5bc8018377d4c12f966bbca2ab)), closes [EX-1748](https://searchbroker.atlassian.net/browse/EX-1748)
* **queries-preview:** add isAnyQueryLoadedInPreview composable (#1229) ([5c728e0](https://github.com/empathyco/x/commit/5c728e0304663c601283f1fae2c4dae297caa5ee))
* **queries-preview:** add loaded previews getter (#1227) ([ab59fa2](https://github.com/empathyco/x/commit/ab59fa2c31440e1b47108cc5c334fe0cfaafad27))
* **queries-preview:** add query preview component  (#699) ([676cda4](https://github.com/empathyco/x/commit/676cda42a3cbd37ee00e3200a89854c6c1bec3ee)), closes [EX-6845](https://searchbroker.atlassian.net/browse/EX-6845)
* **queries-preview:** add wiring and actions (#677) ([a92e350](https://github.com/empathyco/x/commit/a92e3509be65dfce17796efa6fae14a370bc875c)), closes [EX-6844](https://searchbroker.atlassian.net/browse/EX-6844)
* **queries-preview:** allow queries preview with same query but different filters or params (#1392) ([4c1f63a](https://github.com/empathyco/x/commit/4c1f63aaf4e9fc75d3b8298b2ea41c1fc207940a))
* **queries-preview:** create `queriesPreview` module (#670) ([317d961](https://github.com/empathyco/x/commit/317d961e94b0b7454cb4d858d401c4264c74cf0e)), closes [EX-6638](https://searchbroker.atlassian.net/browse/EX-6638)
* **queries-preview:** display tagging from QP request accessible in QP component (#1389) ([27dfec8](https://github.com/empathyco/x/commit/27dfec8dc2725a7c2300e306d82617a2d1de130f))
* **queries-preview:** make the QueryPreviewRequestUpdated not replaceable (#1203) ([ccccd90](https://github.com/empathyco/x/commit/ccccd908110080afd2d5ee06c828e2c2293b67ac))
* query preview components allow adding extra params to the request (#1270) ([84143a2](https://github.com/empathyco/x/commit/84143a2b1ee1b9944ddb431f701b3d27d1c20410))
* **query-preview:** Add `debounceTimeMs` to `QueryPreview` component. (#752) ([ddca375](https://github.com/empathyco/x/commit/ddca375201056d374515b7426df1fac3a1ecf6c1)), closes [EX-7049](https://searchbroker.atlassian.net/browse/EX-7049)
* **query-preview:** add `origin` to `QueryPreview` component (#737) ([9c235bc](https://github.com/empathyco/x/commit/9c235bc9457cc959fa2a386b8dce114ff3bf6df7)), closes [EX-7077](https://searchbroker.atlassian.net/browse/EX-7077)
* **query-preview:** add query preview list component to orchestrate requests (#1084) ([dda5cd7](https://github.com/empathyco/x/commit/dda5cd7c0fa4c91ecdc837a6bfb3493a5db883bd)), closes [EX-7541](https://searchbroker.atlassian.net/browse/EX-7541)
* **query-preview:** use cached query-previews (#1360) ([2579ca4](https://github.com/empathyco/x/commit/2579ca42d52c6f6c428b9129d63dc4a0ddb4788c))
* **query-preview:** use deep equal to compare request (#1291) ([cf3c3e7](https://github.com/empathyco/x/commit/cf3c3e7c738d8b2281183c42f00048b3bff918ea))
* **query-suggestions-actions:** refactor actions to an independent files and add test ([e181808](https://github.com/empathyco/x/commit/e181808b972ab1935fd3bad47cfb7c3b894621ba)), closes [EX-1774](https://searchbroker.atlassian.net/browse/EX-1774)
* **query-suggestions-getters:** refactor getters in separated files and testing ([0bb2ec0](https://github.com/empathyco/x/commit/0bb2ec0da19b47a6304fc9ef3d7b4ec8f4130f9c)), closes [EX-1774](https://searchbroker.atlassian.net/browse/EX-1774)
* **query-suggestions-wiring:** add query suggestions wiring ([d96a53f](https://github.com/empathyco/x/commit/d96a53fe1fc9e94888b2ce610cc7dc0c2a9c56bd)), closes [EX-1709](https://searchbroker.atlassian.net/browse/EX-1709)
* **query-suggestions:** add new extra params in the request ([c15512c](https://github.com/empathyco/x/commit/c15512cd6b633d5eefecf8e9efdef2e921d84901)), closes [EX-4627](https://searchbroker.atlassian.net/browse/EX-4627)
* **query-suggestions:** add query suggestions events ([6ca903a](https://github.com/empathyco/x/commit/6ca903ae5041f47e190fd7c51c83f126f63bed00)), closes [EX-1707](https://searchbroker.atlassian.net/browse/EX-1707)
* **query-suggestions:** add query-suggestion component ([990f39b](https://github.com/empathyco/x/commit/990f39b2e441e3256fae73109e8a2dc042d09b9a)), closes [EX-1711](https://searchbroker.atlassian.net/browse/EX-1711)
* **query-suggestions:** add query-suggestions component ([19ff1e2](https://github.com/empathyco/x/commit/19ff1e21eeb120e58bf36aa2a357cc86ed2d3a1f)), closes [EX-1710](https://searchbroker.atlassian.net/browse/EX-1710)
* **querySuggestions:** hide suggestions that match with any session query (#1600) ([2f51375](https://github.com/empathyco/x/commit/2f51375e04d46e2aba77f08332797285829ebde7))
* **recommendations:** add `updateRecommendation` mutation (#891) ([0e9ceec](https://github.com/empathyco/x/commit/0e9ceec145458a55ccbe4abf8e7b49f64d1717ae))
* **recommendations:** add a scopedSlot `layout` to `Recommendations` component ([f5f29a3](https://github.com/empathyco/x/commit/f5f29a37bbf211bd30658cd71da96b063fa73d9f)), closes [EX-3807](https://searchbroker.atlassian.net/browse/EX-3807)
* **recommendations:** create recommendations x-module ([3b5c24c](https://github.com/empathyco/x/commit/3b5c24c5d5e3660f51f5621f16a257617c325daa)), closes [EX-1917](https://searchbroker.atlassian.net/browse/EX-1917)
* **recommendations:** emit `RecommendationsChanged` (#922) ([11119c3](https://github.com/empathyco/x/commit/11119c353bb26ac5dc3fdd774a513b68a1098771))
* **recommendations:** migrate recommendations x-module to composition api (#1519) ([5d44214](https://github.com/empathyco/x/commit/5d44214092af033d9cbf88ec9f306d15a1ded120))
* **recommendations:** recommendations actions, getters & mutations ([0ffad16](https://github.com/empathyco/x/commit/0ffad16bdb52aa01b81606551bd67e493d1457c3)), closes [EX-1918](https://searchbroker.atlassian.net/browse/EX-1918)
* **recommendations:** recommendations component and its test ([41f62da](https://github.com/empathyco/x/commit/41f62daff7a81d83d38031e7d7e24e104bf5993d)), closes [EX-1919](https://searchbroker.atlassian.net/browse/EX-1919)
* **recommendations:** recommendations extra params and state reset on change. ([a5938ac](https://github.com/empathyco/x/commit/a5938ac1280fc273c633061f411c5a47b15e5d78)), closes [EX-4626](https://searchbroker.atlassian.net/browse/EX-4626)
* **recommendations:** recommendations wiring, emitters and events ([5582c35](https://github.com/empathyco/x/commit/5582c35478f9dfc5290c7ef875838735eb65863a)), closes [EX-1919](https://searchbroker.atlassian.net/browse/EX-1919)
* **refining search-box tests:** refining search-box tests ([3f60595](https://github.com/empathyco/x/commit/3f60595e12e26216a2311f5d3f8e1dea8f717327)), closes [EX-2962](https://searchbroker.atlassian.net/browse/EX-2962)
* **related tags:** added related tags config to set a maximum number of items to render ([e6565e3](https://github.com/empathyco/x/commit/e6565e317aa6527d40f7ecfbe3f84b9da38ff4a6)), closes [EX-3031](https://searchbroker.atlassian.net/browse/EX-3031)
* **related-tags:** add `isCurated` property to related tags ([e063f45](https://github.com/empathyco/x/commit/e063f4560573bcb1bf32fbe49753f2fe6b235cc7)), closes [EX-4940](https://searchbroker.atlassian.net/browse/EX-4940)
* **related-tags:** add e2e testing for the related tags ([9048c0a](https://github.com/empathyco/x/commit/9048c0a9c0a794b12ca6543fe18f0ecf86b5001d)), closes [EX-1968](https://searchbroker.atlassian.net/browse/EX-1968)
* **related-tags:** add empty related tags module ([900bce8](https://github.com/empathyco/x/commit/900bce8b50102a92da71439571240311acbc5912)), closes [EX-1749](https://searchbroker.atlassian.net/browse/EX-1749)
* **related-tags:** add mutations and getters for the related tags module. Add testing for getters ([8c2db6f](https://github.com/empathyco/x/commit/8c2db6f3d51a1881c1655f5b75530c4f1f280b72)), closes [EX-1749](https://searchbroker.atlassian.net/browse/EX-1749)
* **related-tags:** add new extra params in the request ([6d642b5](https://github.com/empathyco/x/commit/6d642b59b3030c5c04f00e38a90253aa2199d0a8)), closes [EX-4625](https://searchbroker.atlassian.net/browse/EX-4625)
* **related-tags:** add related tags actions and testing ([c7579f9](https://github.com/empathyco/x/commit/c7579f9de1b7a88be1ba16b0e03cd4f1fec2e37b)), closes [EX-1750](https://searchbroker.atlassian.net/browse/EX-1750)
* **related-tags:** add related tags state ([6633c5c](https://github.com/empathyco/x/commit/6633c5c44fcb61b844c8534ef1b394d7bf31d0b9)), closes [EX-1749](https://searchbroker.atlassian.net/browse/EX-1749)
* **related-tags:** add wiring and emitters for the related tags ([71117a1](https://github.com/empathyco/x/commit/71117a16ee5ddd29519d06a24f3744dfa06f5cea)), closes [EX-1750](https://searchbroker.atlassian.net/browse/EX-1750)
* **related-tags:** added related-tags component ([d2a13ec](https://github.com/empathyco/x/commit/d2a13ec8dfaff2da1905e89cb241f4fa735cf48b)), closes [EX-1753](https://searchbroker.atlassian.net/browse/EX-1753)
* **related-tags:** added the selected related tags to the request ([c5fb10d](https://github.com/empathyco/x/commit/c5fb10d6c88d81eab28f8ecef9e605d90941935a)), closes [EX-1967](https://searchbroker.atlassian.net/browse/EX-1967)
* remove `x-suggestion` class from `BaseSuggestion` component (#1077) ([31f48e9](https://github.com/empathyco/x/commit/31f48e91ca06348d9122ad301f765b48c2fc963f)), closes [EX-8006](https://searchbroker.atlassian.net/browse/EX-8006)
* remove duplicates from image placeholder/fallback classes (#1032) ([2c5390c](https://github.com/empathyco/x/commit/2c5390c0e5cf2d4bc0b843422d2e99415b6e58ff)), closes [EX-7836](https://searchbroker.atlassian.net/browse/EX-7836)
* remove old adapter package and use the new one (#568) ([1632a59](https://github.com/empathyco/x/commit/1632a594b6905e6403c82b2189300eefd45b3691)), closes [EX-6286](https://searchbroker.atlassian.net/browse/EX-6286)
* Remove vue filters (#635) ([5026e84](https://github.com/empathyco/x/commit/5026e84b7dec3a283af8fdd2f68f84b49d332911)), closes [EX-6508](https://searchbroker.atlassian.net/browse/EX-6508)
* remove x installer from router hooks ([46fc1cf](https://github.com/empathyco/x/commit/46fc1cf73fccb01d1e97cd80916e33be5d617cf8))
* rename `search-types` to `x-types` (#928) ([1ac0008](https://github.com/empathyco/x/commit/1ac00084a4f46f453741c6b04a7c18e88c637cee))
* rename `x-grid` class to `x-grid-list` (#1015) ([dbb5d50](https://github.com/empathyco/x/commit/dbb5d502dd9c1e69c18d137edc8be2e13bceaeb2)), closes [EX-7481](https://searchbroker.atlassian.net/browse/EX-7481)
* Rename lifecycle hook events (#939) ([e626b89](https://github.com/empathyco/x/commit/e626b899849b6742e0bce57d86a8ff89718817bf)), closes [EX-7580](https://searchbroker.atlassian.net/browse/EX-7580)
* **renderless-extra-param:** migrate to composition API (#1546) ([3f111f9](https://github.com/empathyco/x/commit/3f111f98fdf0a4175dce0a5d8711bb8d4e4729df))
* replace `AnimationsMixin` with `useCollapseAnimation` composable (#1468) ([e3ee9d9](https://github.com/empathyco/x/commit/e3ee9d94f9acc4abdcd1c591a754c86d9a6abbb7))
* Replace `layoutsmixin` by `useLayouts` composable (#1480) ([71feaae](https://github.com/empathyco/x/commit/71feaae8493fb683919967bdf52de161a4e4fbf2))
* replace DisableAnimationMixin by useDisableAnimation composable (#1469) ([f498d3f](https://github.com/empathyco/x/commit/f498d3fba5d294391dcfca47f9724558e98f50f0))
* replace extra divs with `NoElement` (#1484) ([cc7042e](https://github.com/empathyco/x/commit/cc7042e5f144f2abc9eb39e3834c8a153795f558))
* Replace FacetsMixin by useFacets composable (#1462) ([bb7e0ce](https://github.com/empathyco/x/commit/bb7e0cede8653d82e436db696e80c1bdbcb9cc41))
* **result-add-to-cart:** add BaseResultAddToCart component ([931c949](https://github.com/empathyco/x/commit/931c9495ef8bae1dc12b8c231b056ce3dbf2e634)), closes [EX-1914](https://searchbroker.atlassian.net/browse/EX-1914)
* **result-image:** add fallback and placeholder components ([a2e192e](https://github.com/empathyco/x/commit/a2e192e17c1a219c8f35163b8f6135dfce8d07b2)), closes [EX-4129](https://searchbroker.atlassian.net/browse/EX-4129)
* **result-images:** migrate result images components to composition API (#1496) ([624fb45](https://github.com/empathyco/x/commit/624fb459e71b3c0905e53ba70c1a3a15f581a0fc))
* **result-link:** create BaseResultLink component and events associated with it ([74cf85e](https://github.com/empathyco/x/commit/74cf85eb01950042444ff37a0da41b92201ca5ec)), closes [EX-1911](https://searchbroker.atlassian.net/browse/EX-1911)
* **result:** add `variants` support (#644) ([d5db09e](https://github.com/empathyco/x/commit/d5db09e9be92d0df65329680ee286959030ccecc)), closes [EX-6760](https://searchbroker.atlassian.net/browse/EX-6760)
* **results-list:** add infinite scroll to `ResultsList` component ([2439b5f](https://github.com/empathyco/x/commit/2439b5f8d0aa0a6ca91382d8c7e830e583fdafb4)), closes [EX-3788](https://searchbroker.atlassian.net/browse/EX-3788)
* **results-list:** added results-list component ([d40c5df](https://github.com/empathyco/x/commit/d40c5dfee605f064236980edba581e93a0018346)), closes [EX-3172](https://searchbroker.atlassian.net/browse/EX-3172)
* **result:** set configuration for base-result-link to ignore tagging of click (#1211) ([3319bf8](https://github.com/empathyco/x/commit/3319bf81d2042fcc32eadffa4dfa1bf1b4afb2a4))
* **sanitize:** add sanitize function to encode characters in a string ([fb0344c](https://github.com/empathyco/x/commit/fb0344ce1a86a1ebd702994dab6bee0b9849a528)), closes [EX-1721](https://searchbroker.atlassian.net/browse/EX-1721)
* **scroll:**  add `MainScroll` and `MainScrollItem` ([477c804](https://github.com/empathyco/x/commit/477c804cc6bbd09b1558e1448ce4bfe94e56e85b)), closes [EX-4998](https://searchbroker.atlassian.net/browse/EX-4998)
* **scroll:** add empty `XModule` ([18e3e6a](https://github.com/empathyco/x/commit/18e3e6a4c17fccc8fedf90b9d644de41b224f716)), closes [EX-4996](https://searchbroker.atlassian.net/browse/EX-4996)
* **scroll:** add new component `base-scroll-to-top` ([6c7b97c](https://github.com/empathyco/x/commit/6c7b97c624d7bee7b24091cc9fde521b3e982136)), closes [EX-3197](https://searchbroker.atlassian.net/browse/EX-3197)
* **scroll:** add new component base-scroll ([7b95385](https://github.com/empathyco/x/commit/7b9538591d89caa132ef89a3674bbeea8e7bd076)), closes [EX-3191](https://searchbroker.atlassian.net/browse/EX-3191)
* **scroll:** add scroll data state to the alias API ([7f5642c](https://github.com/empathyco/x/commit/7f5642cf5e60fe96a22c8fe9897c9ba73cbede55)), closes [EX-5249](https://searchbroker.atlassian.net/browse/EX-5249)
* **scroll:** add top offset when automatically scrolling to main-scroll-item (#1277) ([42dc680](https://github.com/empathyco/x/commit/42dc680e3ee3af4ccda6454d967da0750d2bba7e))
* **scroll:** capture listeners in MainScrollItem component (#942) ([2719a3d](https://github.com/empathyco/x/commit/2719a3dd6c1408f9413ecbee4ebf3c46bf24eea2))
* **scroll:** ignore first visible element when it is also the first one observed ([4ae670c](https://github.com/empathyco/x/commit/4ae670c87c534ca551da2b6ee44596ff56505f92)), closes [EX-5041](https://searchbroker.atlassian.net/browse/EX-5041)
* **scroll:** move scroll related components to the `Scroll` `XModule` ([be083fa](https://github.com/empathyco/x/commit/be083fa6f46d7fc1f6d7a2a4288f7d09644da042)), closes [EX-4997](https://searchbroker.atlassian.net/browse/EX-4997)
* **scroll:** remove animations on pending element to scroll ([7a33653](https://github.com/empathyco/x/commit/7a336531c4fedb2c38133a5464f9b7e9736cef68)), closes [EX-5025](https://searchbroker.atlassian.net/browse/EX-5025)
* **scroll:** replace `ScrollMixin` by `UseScroll` composable (#1473) ([26244cd](https://github.com/empathyco/x/commit/26244cdc8ced863918f0ceb8138ca89bf6792461))
* **search-box-config:** add default config for search-box x-module ([41b13f7](https://github.com/empathyco/x/commit/41b13f7e0d79db9458628da3850462bf9291d695)), closes [EX-1678](https://searchbroker.atlassian.net/browse/EX-1678)
* **search-box-module-events:** add new events of search-box module ([0893ecf](https://github.com/empathyco/x/commit/0893ecf474be559bd46674cad00bf4a356aec03c)), closes [EX-1679](https://searchbroker.atlassian.net/browse/EX-1679)
* **search-box-wiring:** add wires in search-box wiring ([fe37811](https://github.com/empathyco/x/commit/fe3781105d7a62e2a12466d2411e08b2102c0e73)), closes [EX-1664](https://searchbroker.atlassian.net/browse/EX-1664)
* **search-box:** add `SearchInputPlaceholder` component (#771) ([a2e73e3](https://github.com/empathyco/x/commit/a2e73e3895c5454898fbc7ddc6d2202e03448fff)), closes [EX-7178](https://searchbroker.atlassian.net/browse/EX-7178)
* **search-box:** add event UserClearedQuery to be emitted when search-box is cleared in any way ([23502e9](https://github.com/empathyco/x/commit/23502e9271879cb79203f57e8bba82f727dd9e33)), closes [EX-1916](https://searchbroker.atlassian.net/browse/EX-1916)
* **search-box:** add input status handling(#903) ([c74b8fb](https://github.com/empathyco/x/commit/c74b8fbc9734541774c535792466333b78197146)), closes [EX-6474](https://searchbroker.atlassian.net/browse/EX-6474)
* **search-box:** add instant search to SearchInput component ([bf58c4c](https://github.com/empathyco/x/commit/bf58c4c609b292b277ff18fae0c92010ef8cefb3)), closes [EX-1934](https://searchbroker.atlassian.net/browse/EX-1934)
* **search-box:** focus search input after clicking clear search button ([d28994c](https://github.com/empathyco/x/commit/d28994c1995834a1adb19798060051089200d7f7)), closes [EX-2242](https://searchbroker.atlassian.net/browse/EX-2242)
* **search-box:** migrate search-box x-module components to Composition API (#1476) ([5c2b7bc](https://github.com/empathyco/x/commit/5c2b7bcf47281f9a3bb2ea65a1bfb73c6d850260))
* **search-button:** add search-button component ([1c9d7e7](https://github.com/empathyco/x/commit/1c9d7e79939c5b8440a1aea20e4ef211273234eb)), closes [EX-1662](https://searchbroker.atlassian.net/browse/EX-1662)
* **search-input:** add property autofocus ([7863b08](https://github.com/empathyco/x/commit/7863b080eea15317bfe1b6fbf0f2b60b5e8f8944)), closes [EX-2129](https://searchbroker.atlassian.net/browse/EX-2129)
* **search-input:** add search input component ([54ba47a](https://github.com/empathyco/x/commit/54ba47aa30aa23076bf990bfb6d9471a108c024f)), closes [EX-1661](https://searchbroker.atlassian.net/browse/EX-1661)
* **search-input:** prevent `<` or `>` input (#433) ([afc865f](https://github.com/empathyco/x/commit/afc865f2e13d775e5ee4a602536dfd2ee8b474b8)), closes [EX-7035](https://searchbroker.atlassian.net/browse/EX-7035)
* **search-module:** Add banners an promoteds in store. ([857e657](https://github.com/empathyco/x/commit/857e657dfbf1739970490a05391a4e4e1b641269)), closes [EX-3175](https://searchbroker.atlassian.net/browse/EX-3175)
* **search-types:** include the search-types.api.json file to generate the package documentation ([26dd188](https://github.com/empathyco/x/commit/26dd18876c9153255a39817a55512ece28725d93)), closes [EX-1776](https://searchbroker.atlassian.net/browse/EX-1776)
* **search:** add `BannersList` and `PromotedsList` components ([5794f31](https://github.com/empathyco/x/commit/5794f312d21e8b4ec64192ec0533a6f762b39959)), closes [EX-4293](https://searchbroker.atlassian.net/browse/EX-4293)
* **search:** Add `page` and `pageSize` properties with its mutations. ([8a35cf5](https://github.com/empathyco/x/commit/8a35cf5d1da1bd1c68249ae60bdc2eaa639824d8)), closes [EX-3775](https://searchbroker.atlassian.net/browse/EX-3775)
* **search:** add `PartialResultsList` component ([b5e1976](https://github.com/empathyco/x/commit/b5e1976e5cbf67d264011483ee7d613673ae9777)), closes [EX-3354](https://searchbroker.atlassian.net/browse/EX-3354)
* **search:** add `Promoted` component ([9c887dc](https://github.com/empathyco/x/commit/9c887dc77e66bf4847a0592557f68461844e0c44)), closes [EX-4289](https://searchbroker.atlassian.net/browse/EX-4289)
* **search:** add `SearchTaggingChanged`  emitter and save coming `queryTagging` from the search response ([aeb8cea](https://github.com/empathyco/x/commit/aeb8cea22fbc5abe3e8144000984cbff0e9f37d6)), closes [EX-3525](https://searchbroker.atlassian.net/browse/EX-3525)
* **search:** add `SortDropdown` component ([896a06b](https://github.com/empathyco/x/commit/896a06b451e71df1f721eaa8e53841ec07ab7a44)), closes [EX-3299](https://searchbroker.atlassian.net/browse/EX-3299)
* **search:** add `Spellcheck` component ([0a11ecd](https://github.com/empathyco/x/commit/0a11ecdbca7e0f8d14061fa9642338e9aa146b12)), closes [EX-3179](https://searchbroker.atlassian.net/browse/EX-3179)
* **search:** add `SpellcheckButton` component ([8eeca50](https://github.com/empathyco/x/commit/8eeca50c0d961ce258946407797b2d7f086e8731)), closes [EX-3329](https://searchbroker.atlassian.net/browse/EX-3329)
* **search:** add `updateResult` mutation (#706) ([809e346](https://github.com/empathyco/x/commit/809e34694e5a54bd72e92272aa69a9123bef94c4)), closes [EX-6894](https://searchbroker.atlassian.net/browse/EX-6894)
* **search:** add Banner component (#42) ([205bf13](https://github.com/empathyco/x/commit/205bf13fe72a5d2c9b28fd0866a9ceb2d14b1700)), closes [EX-4291](https://searchbroker.atlassian.net/browse/EX-4291)
* **search:** add basic search x-module ([f2974d8](https://github.com/empathyco/x/commit/f2974d8ad22ae3c02efda5353c4642728637b02d)), closes [EX-2167](https://searchbroker.atlassian.net/browse/EX-2167)
* **search:** add extra params to search module ([1c44a70](https://github.com/empathyco/x/commit/1c44a708a4df63b879fccc8617bf1b1fb12747a0)), closes [EX-4554](https://searchbroker.atlassian.net/browse/EX-4554)
* **search:** add fallback disclaimer component (#1122) ([206db77](https://github.com/empathyco/x/commit/206db772b80cfe8a4cab23db19842ea8bd909733)), closes [EX-8080](https://searchbroker.atlassian.net/browse/EX-8080)
* **search:** add new PartialQueryButton component ([931fd02](https://github.com/empathyco/x/commit/931fd02eb69d6f686dfb8aba6be5a333c3b9d689)), closes [EX-3568](https://searchbroker.atlassian.net/browse/EX-3568)
* **search:** add new SortList component ([3ff87bc](https://github.com/empathyco/x/commit/3ff87bc0f89e931f432f41c31038ca29bb17d3ea)), closes [EX-3298](https://searchbroker.atlassian.net/browse/EX-3298)
* **search:** add origin to the request ([eb81c7e](https://github.com/empathyco/x/commit/eb81c7e1dacdf0cc201995c9ac5dfe9bb4f64a2d)), closes [EX-4637](https://searchbroker.atlassian.net/browse/EX-4637)
* **search:** add Redirection and AutoProgressBar components ([14168eb](https://github.com/empathyco/x/commit/14168eb6bc9ead3c807f70765cc6f277532c2959)), closes [EX-4297](https://searchbroker.atlassian.net/browse/EX-4297)
* **search:** add SelectedFiltersChanged wiring ([af266d2](https://github.com/empathyco/x/commit/af266d2f36a877511d0d5fef9361687116565d7f))
* **search:** add sort picker list component (#1155) ([03beec8](https://github.com/empathyco/x/commit/03beec816b07d6532d01b97034110a354d52024c))
* **search:** add store logic & wiring to support sorting results ([c20cb1c](https://github.com/empathyco/x/commit/c20cb1c32e73313462669162eac58b466af19bbf)), closes [EX-3301](https://searchbroker.atlassian.net/browse/EX-3301)
* **search:** add the capability to reload the current search (#1515) ([617c3b0](https://github.com/empathyco/x/commit/617c3b0d4c07a1054d95c9b4316b86dc5112643e))
* **search:** add total results in store and in the alias ([a771f1d](https://github.com/empathyco/x/commit/a771f1d1344528f757a1a42734f44f4fd7d6a710)), closes [EX-3187](https://searchbroker.atlassian.net/browse/EX-3187)
* **search:** change `saveOriginWire` wire from `SelectedRelatedTagsChanged` to `UserPickedARelatedTag`  (#254) ([86072b0](https://github.com/empathyco/x/commit/86072b0805a3dc61b75c0a5760cf2c70e125be34)), closes [EX-5078](https://searchbroker.atlassian.net/browse/EX-5078)
* **search:** extract `fetchAndSaveResponse` `onSuccess` callback to its own `saveSearchResponse` action (#461) ([d24560f](https://github.com/empathyco/x/commit/d24560f3a091e84bc1e43cfae5c380c0262cc3b0)), closes [EX-5982](https://searchbroker.atlassian.net/browse/EX-5982)
* **search:** handle display tagging from search response (#1388) ([b6b5d86](https://github.com/empathyco/x/commit/b6b5d8657947b8510f9d23530d709e757e5e3ecf))
* **search:** make `banners`, `promoteds` , `redirections`, `spellcheck` and `partialResults` optionals in `SearchResponse`  ([2d205c3](https://github.com/empathyco/x/commit/2d205c3141f69e05624dfb91987ebf14aee5fc34)), closes [EX-5976](https://searchbroker.atlassian.net/browse/EX-5976)
* **search:** remove search results getter and replace the access to them with the State decorator ([2b6a8e9](https://github.com/empathyco/x/commit/2b6a8e9d2d67fffa3a10f177a3fabdccc55a3d16)), closes [EX-3053](https://searchbroker.atlassian.net/browse/EX-3053)
* **search:** save `Redirection`'s entities ([cdba4a6](https://github.com/empathyco/x/commit/cdba4a656f7cea74115d06173151d450657d1aed)), closes [EX-4730](https://searchbroker.atlassian.net/browse/EX-4730)
* **search:** update search getter in order to use the new page and pageSize properties of the module ([8fcff62](https://github.com/empathyco/x/commit/8fcff62f68697d983629047a36ca4d7ec22caeea)), closes [EX-3787](https://searchbroker.atlassian.net/browse/EX-3787)
* **semantic-queries:** add maxItemsToRequest config (#1224) ([a124636](https://github.com/empathyco/x/commit/a124636d60170cc3f54a9d8a1e10351926f97aba))
* **semantic-queries:** add semantic queries module and component (#1213) ([f1dc4a7](https://github.com/empathyco/x/commit/f1dc4a7e10e57d69bda37925fbb1113fc778b5c1))
* **semantic-queries:** add SemanticQuery component (#1226) ([09ed3b4](https://github.com/empathyco/x/commit/09ed3b4ad9c01cc116d29a1b618c6dae48e14829))
* send totalHits -1 when there are no results and semantics (#1425) ([d393649](https://github.com/empathyco/x/commit/d39364944d2ee76ee5412480e9c3cdeb55fc4fa1))
* show next result image on hover (#863) ([8fd02cc](https://github.com/empathyco/x/commit/8fd02cc8f9913dfa0e06af83251db4577656099e)), closes [EX-5970](https://searchbroker.atlassian.net/browse/EX-5970)
* **simple-filter:** migrate RenderlessFilter and SimpleFilter to composition API(#1529) ([8d3a2f2](https://github.com/empathyco/x/commit/8d3a2f23748eec700be10f83cad909b6fdf2aa9b))
* **sliced-filters:** add dynamic prop to show more/less buttons (#1146) ([08de5f8](https://github.com/empathyco/x/commit/08de5f827d4ce6b33f04c60655628dabeb19a3bd))
* **sliding-panel:** add SlidingPanel component ([5fde202](https://github.com/empathyco/x/commit/5fde2025f3a062d268921d5e80fe971738a18f84)), closes [EX-2201](https://searchbroker.atlassian.net/browse/EX-2201)
* **sliding-panel:** migrate sliding-panel component to composition API (#1485) ([bf9e1a3](https://github.com/empathyco/x/commit/bf9e1a38364a23402562a19ce8095452da5f02d7))
* **spatial-navigation:** ability to move between any component and the keyboard-navigation component ([3b8defb](https://github.com/empathyco/x/commit/3b8defb6f8d0bf3d646fa6f09bbbcc107f460b34))
* **spellcheck:** add spellchecked query to Alias API ([226f1fe](https://github.com/empathyco/x/commit/226f1fe2ddc5426472fd5819a999102395d0fdab)), closes [EX-4694](https://searchbroker.atlassian.net/browse/EX-4694)
* **standard-version:** append ci type into standard version configuration ([37dad1e](https://github.com/empathyco/x/commit/37dad1e311f31556deeed34097f6d83d6ed77421)), closes [EX-1723](https://searchbroker.atlassian.net/browse/EX-1723)
* standardise all events links in component docs section (#1265) ([ff90da2](https://github.com/empathyco/x/commit/ff90da215d5c16b01f226a85d8656d10817521d0))
* **storage-service:** Rename `StorageService` to `BrowserStorageService` ([6bf38fb](https://github.com/empathyco/x/commit/6bf38fb7d14323c84c949e21eaa9c692fb0014d7)), closes [EX-5073](https://searchbroker.atlassian.net/browse/EX-5073)
* **suggestions:** add suggestions generic component ([2a9e93c](https://github.com/empathyco/x/commit/2a9e93c8ab4ed80c64e3ba3ab187f6b9ab7a4025)), closes [EX-1692](https://searchbroker.atlassian.net/browse/EX-1692)
* **tabs-panel:** add base tabs panel component (#871) ([ebd5feb](https://github.com/empathyco/x/commit/ebd5feb4006315236ae62f8de03d6a986d9ced10)), closes [EX-6142](https://searchbroker.atlassian.net/browse/EX-6142)
* **tagging:** `track` query ([594c656](https://github.com/empathyco/x/commit/594c65649cbf08f586dc9912b367ea39d9da2fa6)), closes [EX-4989](https://searchbroker.atlassian.net/browse/EX-4989)
* **tagging:** add `SessionService` ([b9fcbfc](https://github.com/empathyco/x/commit/b9fcbfc0d600a0a4b32245d56c5b00965217e5f5)), closes [EX-4875](https://searchbroker.atlassian.net/browse/EX-4875)
* **tagging:** add basic tagging x-module ([0fd702f](https://github.com/empathyco/x/commit/0fd702f332ae40ce07d0688d117f3af45d8e7698)), closes [EX-3195](https://searchbroker.atlassian.net/browse/EX-3195)
* **tagging:** add feature hardcoded values ([ee6db3a](https://github.com/empathyco/x/commit/ee6db3a360228528a109fedc732bd552ad5d5a61)), closes [EX-5003](https://searchbroker.atlassian.net/browse/EX-5003)
* **tagging:** add new `SearchTaggingReceived` event for tracking the query ([d58b697](https://github.com/empathyco/x/commit/d58b69730915ccd6fb2b0656ff7280450275b5be)), closes [EX-5170](https://searchbroker.atlassian.net/browse/EX-5170)
* **tagging:** add new type values to ResultFeature and FeatureLocation (#1209) ([a48dc72](https://github.com/empathyco/x/commit/a48dc720b10d7e8ad59445f684cee3fc18d9bb8d))
* **tagging:** Include 'location' parameter to track result events. (#273) ([69bab4b](https://github.com/empathyco/x/commit/69bab4b81f85725f3fc0a9bdc3177db09dd46a40)), closes [EX-5163](https://searchbroker.atlassian.net/browse/EX-5163) [EX-5163](https://searchbroker.atlassian.net/browse/EX-5163)
* **tagging:** make `tagging` and `queryTagging` optional (#797) ([0e49156](https://github.com/empathyco/x/commit/0e49156308d4e77d667a2191697101674cdbf213)), closes [EX-7231](https://searchbroker.atlassian.net/browse/EX-7231)
* **tagging:** migrate to composition API (#1543) ([f06e35d](https://github.com/empathyco/x/commit/f06e35d25fb561bca1b53f579ed7ace8674b9085))
* **tagging:** move `origin` from `request.getter` to `fetchAndSave.action` ([b0bb40d](https://github.com/empathyco/x/commit/b0bb40de5e2ae7f65e2e2df032a1da9a51f0cb4d)), closes [EX-5079](https://searchbroker.atlassian.net/browse/EX-5079)
* **tagging:** send query event when a result from a QP is clicked (#1409) ([2236948](https://github.com/empathyco/x/commit/22369482f51fc2e9b36c7b8280ad0da3ab5e504d))
* **tagging:** track banner clicks (#822) ([504d6bf](https://github.com/empathyco/x/commit/504d6bf29ca86ece7b8116cb32a676f05624468d))
* **tagging:** track displayClick (#1222) ([e9a569e](https://github.com/empathyco/x/commit/e9a569e2b4d7b25b39aae9cad90dbd7da7203b3c))
* **tagging:** track displayClick properties in result & tagging request (#1225) ([53a209e](https://github.com/empathyco/x/commit/53a209e5c9719a8ba0cff21f5d8d52b0dfe70c6d))
* **tagging:** track pending query ([e6c8fd4](https://github.com/empathyco/x/commit/e6c8fd401b28b2e931ebf78697f218f53134cc5a)), closes [EX-4963](https://searchbroker.atlassian.net/browse/EX-4963)
* **tagging:** track result click events ([81f009b](https://github.com/empathyco/x/commit/81f009b0a6264c44436082e457bcb4a12daf5d19)), closes [EX-3527](https://searchbroker.atlassian.net/browse/EX-3527)
* **tagging:** track the 'UserClickedResultAddToCart'event in tagging ([873d345](https://github.com/empathyco/x/commit/873d345d67199a64fe9f10c70944b4f74f290405)), closes [EX-3529](https://searchbroker.atlassian.net/browse/EX-3529)
* **term-suggestions-config:** add term-suggestions config ([c695bbc](https://github.com/empathyco/x/commit/c695bbc221b6665338084ec8272acbcded3da38a)), closes [EX-1708](https://searchbroker.atlassian.net/browse/EX-1708)
* **test-utils:** add utility functions to make easier testing with jest ([21cbf33](https://github.com/empathyco/x/commit/21cbf336dff6ad15679dcb87429251a78dbe8747)), closes [EX-1788](https://searchbroker.atlassian.net/browse/EX-1788)
* **test:** e2e test for exclude-filters-with-no-results component ([9fffe27](https://github.com/empathyco/x/commit/9fffe274160ffd8e23215048b46c47ff8ab146bd)), closes [EX-3599](https://searchbroker.atlassian.net/browse/EX-3599)
* **test:** refactor base tests to cypress component testing ([dc7a924](https://github.com/empathyco/x/commit/dc7a924b612411470742d222bcc6531fa656ce13)), closes [EX-4928](https://searchbroker.atlassian.net/browse/EX-4928)
* **toggle-panel:** base toggle panel component ([139f457](https://github.com/empathyco/x/commit/139f45706f6ef4aa81037c9b459f4de9aaf8eeb9)), closes [EX-2658](https://searchbroker.atlassian.net/browse/EX-2658)
* **ts-doc:** add support to tsdoc and jsdoc eslint plugins ([aa89066](https://github.com/empathyco/x/commit/aa89066c7dc9d67e5aafa0599542cef8fef44cbd)), closes [EX-1689](https://searchbroker.atlassian.net/browse/EX-1689)
* **ts-es-lint:** add support to TypeScript ES-lint through new plugin ([7a6b3bc](https://github.com/empathyco/x/commit/7a6b3bcf8b92bccfc581b870496e357a4e15f301)), closes [EX-1619](https://searchbroker.atlassian.net/browse/EX-1619)
* update `Tagging` model ([598915c](https://github.com/empathyco/x/commit/598915ced128e3fa5586ff6c870e68cfa2e016c3)), closes [EX-4985](https://searchbroker.atlassian.net/browse/EX-4985)
* update polyfills plugin to work with chunks ([54c1842](https://github.com/empathyco/x/commit/54c18420011e5e452bd8b48d640cbd067d0ce921)), closes [EX-5278](https://searchbroker.atlassian.net/browse/EX-5278)
* update result information in the QPs (#1591) ([3e99d0c](https://github.com/empathyco/x/commit/3e99d0cdcb25366af2adff977e25d58d45f7421f))
* update to rollup 4 (#1370) ([a5c471b](https://github.com/empathyco/x/commit/a5c471b7d139393b7c2c0dffd88973029f2ced31))
* update typescript ([73edca6](https://github.com/empathyco/x/commit/73edca61c1cea39d82a7ab94bc18c8bff94c138c)), closes [EX-5367](https://searchbroker.atlassian.net/browse/EX-5367)
* update x-components browserslist  ([0795ed3](https://github.com/empathyco/x/commit/0795ed3b2cca9d64069426e1b449bbcc725f0a09)), closes [EX-3929](https://searchbroker.atlassian.net/browse/EX-3929)
* **url:** add `url` x-module config. (#129) ([6570590](https://github.com/empathyco/x/commit/6570590738f3667419427fcde74fafe96e851f3c)), closes [EX-4578](https://searchbroker.atlassian.net/browse/EX-4578)
* **url:** Add an action to save from url to the store. ([9fbf8d4](https://github.com/empathyco/x/commit/9fbf8d448bd243a3850eebbe1a4520372260e28a)), closes [EX-4712](https://searchbroker.atlassian.net/browse/EX-4712)
* **url:** add new empty module ([955a3bf](https://github.com/empathyco/x/commit/955a3bf35930be8688ad8fefc20632573e8e899b)), closes [EX-3203](https://searchbroker.atlassian.net/browse/EX-3203)
* **url:** add new events ([702a8a8](https://github.com/empathyco/x/commit/702a8a8342b63831c78f6c3b018351787cd27c0a)), closes [EX-4562](https://searchbroker.atlassian.net/browse/EX-4562)
* **url:** add new URL Manager component  ([b3ea10d](https://github.com/empathyco/x/commit/b3ea10dfa0f94d13104372e6bde1733a2c013dae)), closes [EX-4566](https://searchbroker.atlassian.net/browse/EX-4566)
* **url:** add url module state, urlParams getter and its emitter ([2c549ec](https://github.com/empathyco/x/commit/2c549eca859aafd68e67eddf4882d9ae43827991)), closes [EX-4570](https://searchbroker.atlassian.net/browse/EX-4570)
* **url:** refactor module logic movig some logic to UrlHandler Component ([f5c9d61](https://github.com/empathyco/x/commit/f5c9d61e96a5365100bc832a955f03161100be79)), closes [EX-4864](https://searchbroker.atlassian.net/browse/EX-4864)
* **url:** set `origin` when navigating ([02aa766](https://github.com/empathyco/x/commit/02aa7661a15c3718f4809d094a01b0f684a1f55d)), closes [EX-3541](https://searchbroker.atlassian.net/browse/EX-3541)
* **url:** set sort values and read them from the url ([6d98ca3](https://github.com/empathyco/x/commit/6d98ca3e031a9075c27f436419818e2d85b610cc)), closes [EX-3517](https://searchbroker.atlassian.net/browse/EX-3517)
* **url:** set the related tags from the url in the store and viceversa ([ec3baa8](https://github.com/empathyco/x/commit/ec3baa84732019b3c2c599c3e809124ede199fa3)), closes [EX-3509](https://searchbroker.atlassian.net/browse/EX-3509)
* **url:** syncronize url and state with the facets and remove query from facets module ([370db5d](https://github.com/empathyco/x/commit/370db5d73a2cad96173db41b1869f1f665213c22)), closes [EX-3511](https://searchbroker.atlassian.net/browse/EX-3511)
* **url:** syncronize url and state with the page ([16bc309](https://github.com/empathyco/x/commit/16bc309a0b592e98b3d25d937b2da0f7d2cbd5e4)), closes [EX-3519](https://searchbroker.atlassian.net/browse/EX-3519)
* **url:** syncronize url and state with the page ([2590cdc](https://github.com/empathyco/x/commit/2590cdc8e6c7effb075c3c4407ad1379e0fa3201)), closes [EX-3519](https://searchbroker.atlassian.net/browse/EX-3519)
* **url:** syncronize url and state with the query ([95af0c5](https://github.com/empathyco/x/commit/95af0c5094c4dc1fccbde5a4ed75178f6a041661)), closes [EX-3509](https://searchbroker.atlassian.net/browse/EX-3509)
* Use Banner position (= row) to sort grid (#802) ([28836a7](https://github.com/empathyco/x/commit/28836a71b91f210f425098f41ab71136a1b7b34c)), closes [EX-7292](https://searchbroker.atlassian.net/browse/EX-7292)
* use cancellable-promise in every request action ([eca7f1b](https://github.com/empathyco/x/commit/eca7f1ba8393b03aaae09e56ad63ea2b61a74335)), closes [EX-2664](https://searchbroker.atlassian.net/browse/EX-2664)
* **use-debounce:** create useDebounce composable to deprecate Debounce decorator (#1475) ([67f0e42](https://github.com/empathyco/x/commit/67f0e42079839ec9c0f74a9d25ecf9bb2de9a9ab))
* **use-x-bus:** unsubscribe from bus events when component is unmounted (#1472) ([36f542a](https://github.com/empathyco/x/commit/36f542ad255096816fccba4c7dcec8e5a9571550))
* utils for the mutation of states with config (#1313) ([97dfb3e](https://github.com/empathyco/x/commit/97dfb3e2d37f6ec037f55ccc3279b9427d90d1c5))
* **utils:** add array and normalize shared utility functions ([cb64273](https://github.com/empathyco/x/commit/cb6427373dc6307858252a70592a271ccbad30e4)), closes [EX-1764](https://searchbroker.atlassian.net/browse/EX-1764)
* **utils:** add callback for cancellable promises. ([dd6e9d7](https://github.com/empathyco/x/commit/dd6e9d75305aa465bb416b6171db7f7487690255)), closes [EX-2380](https://searchbroker.atlassian.net/browse/EX-2380)
* **utils:** add debounce util ([00d862b](https://github.com/empathyco/x/commit/00d862b8c5c2b258afd908a97e85a836aeb27492)), closes [EX-1934](https://searchbroker.atlassian.net/browse/EX-1934)
* **utils:** log request errors by default (#458) ([872c0b9](https://github.com/empathyco/x/commit/872c0b9e64112388c641434c2e0cb81ea92d9c20)), closes [EX-5981](https://searchbroker.atlassian.net/browse/EX-5981)
* **utils:** now `origin` only requires the `feature` ([087d646](https://github.com/empathyco/x/commit/087d646a2b97f945e9c4f81112925a6783d66f41)), closes [EX-5077](https://searchbroker.atlassian.net/browse/EX-5077)
* **vue-styleguidist:** add vue styleguidist to document components ([58b65f5](https://github.com/empathyco/x/commit/58b65f54835af512344cc0ba8401ed9140b0f366)), closes [EX-1576](https://searchbroker.atlassian.net/browse/EX-1576)
* wai-aria for BaseEventButton based components (#816) ([3dfd29e](https://github.com/empathyco/x/commit/3dfd29e8f8cc57c5caeeda609ccd4903434bd74a)), closes [EX-7204](https://searchbroker.atlassian.net/browse/EX-7204)
* **wires-factory:** add implementation to NamespacedWireFactory.wireCommit with a function payload ([c882810](https://github.com/empathyco/x/commit/c8828104c6c28b3124b704e5b3c873c3531f9215)), closes [EX-1594](https://searchbroker.atlassian.net/browse/EX-1594)
* **wiring-operators:** add filterWhitelistedModules & filterBlacklistedModules operators ([06e2c84](https://github.com/empathyco/x/commit/06e2c8475aa7489b50bcee4853d7d0c2b59e3dc9)), closes [EX-1618](https://searchbroker.atlassian.net/browse/EX-1618)
* **wiring:** add force and cancel support to debounce and throttle wire operators. Update rxjs to v7. ([1fe2f29](https://github.com/empathyco/x/commit/1fe2f298589b1aa44798f3911379fe11905a43a9)), closes [EX-5123](https://searchbroker.atlassian.net/browse/EX-5123)
* **wiring:** add option to pass a function with the store as payload for the wireDispatch factory methods. ([ee5586f](https://github.com/empathyco/x/commit/ee5586f0e293e4d6e42698eb275072a31cf0b30a)), closes [EX-2002](https://searchbroker.atlassian.net/browse/EX-2002)
* **wiring:** add WirePayloadParams type and modified NamespacedWireFactory ([731a485](https://github.com/empathyco/x/commit/731a4856a49be7dfe439f8e49d5d5ccf87a1cd20)), closes [EX-1594](https://searchbroker.atlassian.net/browse/EX-1594)
* **wiring:** allow wiring operators to access store to retrieve data ([fcc3476](https://github.com/empathyco/x/commit/fcc34768b8250c961e5149dc1f928e238f8b05c0)), closes [EX-1888](https://searchbroker.atlassian.net/browse/EX-1888)
* **wiring:** refactor namespaced wiring ([79eea49](https://github.com/empathyco/x/commit/79eea496d8b6088a5454fb37d4781d2b16f83492)), closes [EX-1888](https://searchbroker.atlassian.net/browse/EX-1888)
* **wiring:** refactor namespaced wiring ([69e8930](https://github.com/empathyco/x/commit/69e893039c8593a94aab2c5fb85b4e5f59f682cd)), closes [EX-1888](https://searchbroker.atlassian.net/browse/EX-1888)
* **x-api:** append X API and installX middleware function to install X ([2d924d7](https://github.com/empathyco/x/commit/2d924d7a62f3f8e7d2e256c81f8f5345e18b42f2)), closes [EX-1756](https://searchbroker.atlassian.net/browse/EX-1756)
* **x-component.utils:** add `getXComponentXModuleName` util function ([8e6acd7](https://github.com/empathyco/x/commit/8e6acd76a0a2543522e49bdb5da57f6b4ac424ae)), closes [EX-1617](https://searchbroker.atlassian.net/browse/EX-1617)
* **x-installer:** add option to install asynchronous Vue plugins ([e809261](https://github.com/empathyco/x/commit/e8092615ba733366e70ba1a6084d0b775f37fcf3)), closes [EX-3790](https://searchbroker.atlassian.net/browse/EX-3790)
* **x-installer:** add XInstaller utility ([e383570](https://github.com/empathyco/x/commit/e383570f3a473317126c2c04c29bf7fd73021c79)), closes [EX-2136](https://searchbroker.atlassian.net/browse/EX-2136)
* **x-installer:** make `SnippetConfig` object available for all components ([3feeff2](https://github.com/empathyco/x/commit/3feeff2fd14fff33082afd16d1782ee07b0f87f2)), closes [EX-3553](https://searchbroker.atlassian.net/browse/EX-3553)
* **x-installer:** update to vue3 and adapt x-installer (#1572) ([c6b28e5](https://github.com/empathyco/x/commit/c6b28e5e9a07832e992f27a40d7513dbec90d2f2))
* **x-plugin:** add `initialXModules` to `XPluginOptions` to register `XModules` manually when installing the plugin ([f1f840d](https://github.com/empathyco/x/commit/f1f840d3db8c18454be678b3cc2d6e17cc49881b)), closes [EX-3199](https://searchbroker.atlassian.net/browse/EX-3199)
* **x-plugin:** add a logic to save component configurations to store ([553ddd9](https://github.com/empathyco/x/commit/553ddd9174dfda27bce7a387c89398453c53b3a7)), closes [EX-1603](https://searchbroker.atlassian.net/browse/EX-1603)
* **x-plugin:** add alias API ([b05902e](https://github.com/empathyco/x/commit/b05902ecd7568270e4f462a89c0ae9e54db4ead1)), closes [EX-1920](https://searchbroker.atlassian.net/browse/EX-1920)
* **x-plugin:** add full `history queries` list to `alias API` ([e0e0430](https://github.com/empathyco/x/commit/e0e04301b6158dfc379d495e92c04ec5ef35c4ab)), closes [EX-6610](https://searchbroker.atlassian.net/browse/EX-6610)
* **x-plugin:** Add function as possible value of `domElement` in InstallXOptions.(#836) ([99a96ef](https://github.com/empathyco/x/commit/99a96ef2303f27b656835253203bc73758a337ae))
* **x-plugin:** add results to `Alias API` (#545) ([9993ab6](https://github.com/empathyco/x/commit/9993ab6c31f0b532a9cc12eea2f3fb18dd6fd856)), closes [EX-6324](https://searchbroker.atlassian.net/browse/EX-6324)
* **x-plugin:** Add selected sort (#274) ([b4c0d14](https://github.com/empathyco/x/commit/b4c0d140ca5eba8de189068fef5dd2a6249c1207)), closes [EX-5165](https://searchbroker.atlassian.net/browse/EX-5165)
* **x-plugin:** add snippet config getter to XAPI (#1378) ([a76e1b7](https://github.com/empathyco/x/commit/a76e1b716b9aa86fc6853bcf4d1bb7aaa9478f4a))
* **x-plugin:** Make XPluginMixin to add the component `location` to metadata. ([eb2c03a](https://github.com/empathyco/x/commit/eb2c03a329cd78c42becf09bdf49b860dca74e40)), closes [EX-4869](https://searchbroker.atlassian.net/browse/EX-4869)
* **x-plugin:** Remove `XConfig` ([87f7d36](https://github.com/empathyco/x/commit/87f7d3601d7a11c6f7ebae24931ee43768c6ad43)), closes [EX-4240](https://searchbroker.atlassian.net/browse/EX-4240)
* **x-plugin:** Update Alias API with `noResults`, `redirections` and `partialResults` ([c1ad042](https://github.com/empathyco/x/commit/c1ad0422822e88ec501f31e4b75bddf0ac2b3737)), closes [EX-4946](https://searchbroker.atlassian.net/browse/EX-4946)
* **xon-decorator:** add XOn decorator to handle the subscription/unsubscription of an XEvent ([d65511e](https://github.com/empathyco/x/commit/d65511e96a9782d42b5ec5a0444bafc4009a2bbb)), closes [EX-1724](https://searchbroker.atlassian.net/browse/EX-1724)
* **xplugin-search-adapter:** extract adapter to XPlugin and add subscription to adapterConfigChanged ([cd7790f](https://github.com/empathyco/x/commit/cd7790fbe23f04e1296d8510296e52a32830106e)), closes [EX-1605](https://searchbroker.atlassian.net/browse/EX-1605)


### Bug Fixes

*  Next Queries not being calculated when using Related Tags (#1428) ([50306b6](https://github.com/empathyco/x/commit/50306b600c681c1bd54e209ee048893295a016cb))
* `BaseResultImage` not showing the right size on load (#1176) ([c7ebf54](https://github.com/empathyco/x/commit/c7ebf54f03e23bdf8cd1a64e1e008369ca1a643d))
* `pointer-events` affecting scrolling in sliding panel in `SingleColumnLayout` aside (#614) ([1463bc1](https://github.com/empathyco/x/commit/1463bc1d5dd1fbd9c279077d7240329b853f82be)), closes [EX-6595](https://searchbroker.atlassian.net/browse/EX-6595)
* adjust to new vue render function API (#1596) ([7ec2b97](https://github.com/empathyco/x/commit/7ec2b9719f18275e7843544f26f94c393fef7090))
* **animation:** fix Expected Object, got Function on animations props (#1489) ([4467edc](https://github.com/empathyco/x/commit/4467edcb08c8d4f59044209d0f9a800745f6d6af))
* **animations:** disable  leaving elements listening to click events (#70) ([3d7b92b](https://github.com/empathyco/x/commit/3d7b92b1baa2c86c3fe8e390cec8a203bc62c95e)), closes [EX-4504](https://searchbroker.atlassian.net/browse/EX-4504)
* **animations:** make content-visibility CSS property and createCollapseAnimationMixin work together (#839) ([50d5c87](https://github.com/empathyco/x/commit/50d5c8744e5a8d2c8db5aed33e71bd8a39a76cf3))
* **banners:** fix repeated banners and promoted on page load (#62) ([aec10f1](https://github.com/empathyco/x/commit/aec10f1a6d8b65e32eaf459a2d110cb6ea18111f)), closes [EX-4492](https://searchbroker.atlassian.net/browse/EX-4492)
* **base-currency:** format preference goes prop to be injected by default ([29d5e8d](https://github.com/empathyco/x/commit/29d5e8d576019504ef642af6119c764292f44c51)), closes [EX-5649](https://searchbroker.atlassian.net/browse/EX-5649)
* **base-modal:** add prop to allow the modal to move the focus to an element within it on open (#748) ([0954926](https://github.com/empathyco/x/commit/0954926d7e95ab53e3a8fe263265b63f1a5f20d7))
* **base-toggle-panel:** make `base-toggle-panel` component render a `div` to solve react-wrapper integration issues. ([aee0e7c](https://github.com/empathyco/x/commit/aee0e7cdd3de896329985d50beec7775acaf6360)), closes [EX-2763](https://searchbroker.atlassian.net/browse/EX-2763)
* blur related tag when deselected (#1199) ([e3c3efa](https://github.com/empathyco/x/commit/e3c3efa204c047d537f6cf92b0342327409ff3aa))
* build ([f3b6ea9](https://github.com/empathyco/x/commit/f3b6ea91039dcfb1a2d2a50977b65aec7c5cd4c8))
* **build:** Fix build side effects to include css. ([f79d7b9](https://github.com/empathyco/x/commit/f79d7b9e738485e14ac8f88b343a97d8f55c51e6)), closes [EX-5396](https://searchbroker.atlassian.net/browse/EX-5396)
* **build:** make build fail if api-extractor has errors ([799250c](https://github.com/empathyco/x/commit/799250c51ff658393ed168c3778c43ccc3ec1829)), closes [EX-1803](https://searchbroker.atlassian.net/browse/EX-1803)
* **build:** output es5 code for Vue components ([6f94d23](https://github.com/empathyco/x/commit/6f94d23f83c779e79d77df4e0c402cf5d0976469)), closes [EX-2734](https://searchbroker.atlassian.net/browse/EX-2734)
* **build:** replace style injector with ES5 version ([323de9a](https://github.com/empathyco/x/commit/323de9afaac6a95e1ff2f69be9f1048a63ba93cf)), closes [EX-2752](https://searchbroker.atlassian.net/browse/EX-2752)
* **build:** supports being built on Windows based machines ([6e760fa](https://github.com/empathyco/x/commit/6e760fab8d39162897574abab95884cadd6252b8))
* **build:** use the default `vue-cli` `webpack` configuration in `rollup-plugin-vue` (#961) ([f9a9238](https://github.com/empathyco/x/commit/f9a9238cf4a05a6a35129336f318c9440cb6732d)), closes [EX-7706](https://searchbroker.atlassian.net/browse/EX-7706)
* bus handling of a location ref (#1432) ([b980638](https://github.com/empathyco/x/commit/b98063826f5657088bb613db1a529a446389ed67))
* **clean-search-input:** add emitter for the `UserClearedQuery` event. Allow `UserIsTypingAQuery` to be always emitted. ([16c637b](https://github.com/empathyco/x/commit/16c637bec34ff47f56db748e705118162b7954cf)), closes [EX-2031](https://searchbroker.atlassian.net/browse/EX-2031)
* **components:**  now properly checks if a  has content (#612) ([ad2f6dc](https://github.com/empathyco/x/commit/ad2f6dc522d9da59dde2e2c5f90510c0f93380ab)), closes [EX-6681](https://searchbroker.atlassian.net/browse/EX-6681)
* **components:** `SlidingPanel` buttons were blocking clicks while invisible ([711510c](https://github.com/empathyco/x/commit/711510c72b9b216fe6a4d520e7bcf1cc7e8faaf5)), closes [EX-4096](https://searchbroker.atlassian.net/browse/EX-4096)
* **components:** `SlidingPanel` can now disable the resetting scroll … (#286) ([788eb18](https://github.com/empathyco/x/commit/788eb18bf0e066d932484143d0412497f3dada6e)), closes [EX-5197](https://searchbroker.atlassian.net/browse/EX-5197)
* **components:** `StaggeringTransitionGroup` elements now are positioned correctly in scroll containers ([57d9011](https://github.com/empathyco/x/commit/57d90111f1552a9e31aa7bde6e029c75c3214a63)), closes [EX-4257](https://searchbroker.atlassian.net/browse/EX-4257)
* **components:** Add option to extend transitions with listeners and attributes (#600) ([16d5262](https://github.com/empathyco/x/commit/16d5262ab2213d53c736e89774089313755abeff)), closes [EX-6457](https://searchbroker.atlassian.net/browse/EX-6457)
* **components:** emit initial default value in the ColumnPicker mixin ([e0eb345](https://github.com/empathyco/x/commit/e0eb34532cad4d5d54605e4de5e9bdaa26c066d4)), closes [EX-4114](https://searchbroker.atlassian.net/browse/EX-4114)
* **components:** Export missing layout components ([15986f5](https://github.com/empathyco/x/commit/15986f56b8b78b49abe70936c0bd2ba6d85a6bbb)), closes [EX-5160](https://searchbroker.atlassian.net/browse/EX-5160)
* **components:** fix `transform` transition in `FadeAndSlide` animation component ([a2db4c0](https://github.com/empathyco/x/commit/a2db4c0971b5bed00248d0151e9342bd0c0f18f7)), closes [EX-3989](https://searchbroker.atlassian.net/browse/EX-3989)
* **components:** Fix BaseGrid auto columns CSS. (#308) ([77563f0](https://github.com/empathyco/x/commit/77563f0eb71d806fb2cefb88b750c4852918b8c0)), closes [EX-5295](https://searchbroker.atlassian.net/browse/EX-5295)
* **components:** Fix infinite scroll not working in Android Chrome. (#277) ([19c3d77](https://github.com/empathyco/x/commit/19c3d77f124a1bbc099bae0e5dbb80fb30a132a1)), closes [EX-5181](https://searchbroker.atlassian.net/browse/EX-5181)
* **components:** Fix InfiniteScroll get root element inside Shadow DOM. (#874) ([340293f](https://github.com/empathyco/x/commit/340293ffc1946c69018fcfa67a069f443110763d))
* **components:** Fix open issue when focused on body. Fix `SearchInputPlaceholder` styles. (#1078) ([25aa285](https://github.com/empathyco/x/commit/25aa2851daf713512c42ef394707a9f1fc41fe4b)), closes [EX-8011](https://searchbroker.atlassian.net/browse/EX-8011)
* **components:** Fix the error on console in `BaseResultImage` with `CrossFade` Animation. (#688) ([3bcf6e1](https://github.com/empathyco/x/commit/3bcf6e120918b4257f38ddb5078adfe39a7c8a3f)), closes [EX-6924](https://searchbroker.atlassian.net/browse/EX-6924)
* **components:** fix vue components exports ([ab46028](https://github.com/empathyco/x/commit/ab46028adf562b6c820a04adf1125e29aae2485a)), closes [EX-1884](https://searchbroker.atlassian.net/browse/EX-1884)
* **components:** image flickering on re-rendering (#945) ([3b1b558](https://github.com/empathyco/x/commit/3b1b55857ac1c5169a771c465fa32fb4313ab63c)), closes [EX-7610](https://searchbroker.atlassian.net/browse/EX-7610)
* **components:** make column picker & grid components listen to only `ColumnsNumberProvided` event to fix incorrect columns number on re-mounts ([0d3d366](https://github.com/empathyco/x/commit/0d3d366266cee2e383d442913736d35d2f80ea7c)), closes [EX-4189](https://searchbroker.atlassian.net/browse/EX-4189)
* **components:** modal open buttons can now contain HTML elements inside. Disable page scroll when modals are open. Close modals when either clicked out of them or focus is lost ([727cfd4](https://github.com/empathyco/x/commit/727cfd42cb8783fa2446559494cc712264aec9e0)), closes [EX-3361](https://searchbroker.atlassian.net/browse/EX-3361)
* **components:** reset`BaseResultImage` images state when `result` `prop` changes (#888) ([a783ace](https://github.com/empathyco/x/commit/a783ace74929db22b7ed087b0eb19481078a35f5))
* **components:** restore scroll on `BaseModal` (#736) ([d7b18a1](https://github.com/empathyco/x/commit/d7b18a1630f7da36ecd4c52f5b73b8c101612a86)), closes [EX-7091](https://searchbroker.atlassian.net/browse/EX-7091)
* conflict version (#673) ([fb74dd0](https://github.com/empathyco/x/commit/fb74dd0b992522a9441da1daabe5a8789426324f)), closes [EX-6896](https://searchbroker.atlassian.net/browse/EX-6896)
* **cypress:** fix Cypress webpack/preprocessor config to avoid .ts transpilation file issues ([551c125](https://github.com/empathyco/x/commit/551c125c63d70b9d631914aa0b43737b9bd0cd0f)), closes [EX-1870](https://searchbroker.atlassian.net/browse/EX-1870)
* **debounce:** remove wireDebounce to avoid side effects ([42dfc1c](https://github.com/empathyco/x/commit/42dfc1ce245660aebd147cd1ef8b17425e0d1198)), closes [EX-1955](https://searchbroker.atlassian.net/browse/EX-1955)
* **decorators:** pending `debounced` execution is cancelled when the component is destroyed ([27da789](https://github.com/empathyco/x/commit/27da789412804f3f768d07e8ffd846ea2df8553e)), closes [EX-5215](https://searchbroker.atlassian.net/browse/EX-5215)
* **deps:** remove  `only-allow` pnpm (#1097) ([b2a63d3](https://github.com/empathyco/x/commit/b2a63d308f20804d55a266189ab5d6242f88f6d8)), closes [EX-8082](https://searchbroker.atlassian.net/browse/EX-8082)
* **deps:** update dependency @vueuse/core to v10 (#1219) ([3761f17](https://github.com/empathyco/x/commit/3761f17226e1cba9b13a971e43ddb928d5f2f412))
* **design-system:** fix deprecated typography and picture components (#1090) ([4f1bdb7](https://github.com/empathyco/x/commit/4f1bdb7d69a49e51d39dd2a7f8050b0fce3ef96e)), closes [EX-8053](https://searchbroker.atlassian.net/browse/EX-8053)
* **design-system:** Fix grid styles to stretch cells. ([3292229](https://github.com/empathyco/x/commit/32922290173cc87fe5c82934b9a9e01dc27b3c23)), closes [EX-5239](https://searchbroker.atlassian.net/browse/EX-5239)
* **design-system:** fix issues with components height and layout ([4499b10](https://github.com/empathyco/x/commit/4499b101c9207f080e1995faa3d6639c102e0f2f)), closes [EX-4693](https://searchbroker.atlassian.net/browse/EX-4693)
* **design-system:** Fix padding in Input Group Line variant (#58) ([bea2153](https://github.com/empathyco/x/commit/bea2153b702a37e05cc3240fc6201f5b7f38ed5f)), closes [EX-4459](https://searchbroker.atlassian.net/browse/EX-4459)
* **design-system:** Fix Sliding Panel styles. ([bcf2092](https://github.com/empathyco/x/commit/bcf20925c3baf7847792b7b77b07178d62a27e7e)), closes [EX-5234](https://searchbroker.atlassian.net/browse/EX-5234)
* **design-system:** Fix some style issues and add two missing utilities ([c4ae728](https://github.com/empathyco/x/commit/c4ae728d78b36ee566ca283626e36bf9b6aed07f)), closes [EX-5270](https://searchbroker.atlassian.net/browse/EX-5270)
* **design-system:** fix the stroke and the text decoration in the typography ([88b6e97](https://github.com/empathyco/x/commit/88b6e979876fd102e6998d8afa3fdf5b115e2623)), closes [EX-4176](https://searchbroker.atlassian.net/browse/EX-4176)
* **design-system:** fix typo. Increase `gap` and `padding` tokens up to 10.  Add class for list item flex none ([c47a888](https://github.com/empathyco/x/commit/c47a888c43ceb9f152f55b3831aaf575586942a3)), closes [EX-4720](https://searchbroker.atlassian.net/browse/EX-4720)
* **design-system:** solve `Safari` `gap` issues ([a4a0b1e](https://github.com/empathyco/x/commit/a4a0b1e9a16764612a9d3f67f65e21f13ba5f941)), closes [EX-3894](https://searchbroker.atlassian.net/browse/EX-3894)
* **design-tokens:** fix editable tokens not being displayed in view correctly ([bf6a689](https://github.com/empathyco/x/commit/bf6a68967c539b935bd57eeea68ca7fd68a24dca)), closes [EX-3998](https://searchbroker.atlassian.net/browse/EX-3998)
* **directives:** `InfiniteScroll` now works properly in Safari and with html or body as containers ([4921d31](https://github.com/empathyco/x/commit/4921d315b9732f200b1946e2938d20277f04cace)), closes [EX-3826](https://searchbroker.atlassian.net/browse/EX-3826)
* **directives:** change `infinite-scroll` threshold to avoid decimals bug in `Chrome` ([41b9c6e](https://github.com/empathyco/x/commit/41b9c6ebe295e0887dbf65a4ad54dfdef501ca15)), closes [EX-4489](https://searchbroker.atlassian.net/browse/EX-4489)
* **edocs-live-examples:** Live example was not rendered ([5aa2653](https://github.com/empathyco/x/commit/5aa2653054686a3a6b8ada0478f171518d7733c2))
* exports for experience controls (#1312) ([3f02cea](https://github.com/empathyco/x/commit/3f02cea34463b2fe13b539f348c4f42af1f2dc71))
* **extra-params:** prevent callbacks option from the snippet config to be taken as extra params ([2940d2c](https://github.com/empathyco/x/commit/2940d2c7163904a193c459892792b2153de7d079)), closes [EX-5104](https://searchbroker.atlassian.net/browse/EX-5104)
* **facets:** add missing SelectedFilters component export ([bd519ad](https://github.com/empathyco/x/commit/bd519adb33698a6ea17b3c261ccd3404a98d7820)), closes [EX-2984](https://searchbroker.atlassian.net/browse/EX-2984)
* **facets:** Avoid emitting the `SelectedFiltersChanged` event when facets change for the second time. ([02ab010](https://github.com/empathyco/x/commit/02ab01031a4637252de2845655f4dc3b5e9ec2b8)), closes [EX-3570](https://searchbroker.atlassian.net/browse/EX-3570)
* **facets:** Emit the `SelectedFiltersChanged` event when the user deselects the last filter ([0c785c6](https://github.com/empathyco/x/commit/0c785c66a9cc45c8484e786c85ac56612c86d3de)), closes [EX-3570](https://searchbroker.atlassian.net/browse/EX-3570)
* **facets:** fix `SingleSelectModifier` handling for selecting hierar… (#643) ([d9a18e0](https://github.com/empathyco/x/commit/d9a18e06c5241c5b6db9b93ba67c1d9018360160)), closes [EX-6810](https://searchbroker.atlassian.net/browse/EX-6810)
* **facets:** fix issue with hierarchical filters with no children ([6ec443a](https://github.com/empathyco/x/commit/6ec443aacf0479d01e8f7079799b5db9e5b2b696)), closes [EX-4136](https://searchbroker.atlassian.net/browse/EX-4136)
* **facets:** isNewQuery utility was returning false when only one query was empty ([4f81652](https://github.com/empathyco/x/commit/4f816523886aaff40df72ee857fc10baf748f766)), closes [EX-4160](https://searchbroker.atlassian.net/browse/EX-4160)
* **facets:** new label slot inside the Hierarchical Filter children ([5a1bd81](https://github.com/empathyco/x/commit/5a1bd8160b9d9700197f6766b0ed1604040057e9)), closes [EX-4172](https://searchbroker.atlassian.net/browse/EX-4172)
* **facets:** now service uses only the first filter entity to update the facets. ([c2a19cd](https://github.com/empathyco/x/commit/c2a19cddb3db399fa7d242b7557ea8b2dc760461)), closes [EX-4867](https://searchbroker.atlassian.net/browse/EX-4867)
* **filters:** Editable number range filter should be unique (#1243) ([ec8b788](https://github.com/empathyco/x/commit/ec8b78829d16df0db50cfa35e0bdf5ba64529d26))
* Fix @vue/compat alias for x-components imports ([d6d7e2f](https://github.com/empathyco/x/commit/d6d7e2f26e6944af7453c213b8d0a1d28ff359eb))
* fix base rating component (#1256) ([b1616ca](https://github.com/empathyco/x/commit/b1616cac0310535bf1354c5e084ba0267fc1e01e))
* fix for e2e sliding panel tests ([b9b7b23](https://github.com/empathyco/x/commit/b9b7b23fcc7a32dd999b04dd70ecece0057ae693)), closes [EX-3438](https://searchbroker.atlassian.net/browse/EX-3438)
* Fix multiple issues. ([2f5515e](https://github.com/empathyco/x/commit/2f5515e5bcaca67f085ff3eef4fb52698041292c)), closes [EX-5179](https://searchbroker.atlassian.net/browse/EX-5179)
* Fix recommendations `setParams` wire. Export `LIST_ITEMS_KEY`. ([6262d80](https://github.com/empathyco/x/commit/6262d8076941847900a9f577a6588547e4fb703c)), closes [EX-4724](https://searchbroker.atlassian.net/browse/EX-4724)
* fix type of prop ([fbfca6f](https://github.com/empathyco/x/commit/fbfca6f09f3d5145f87b4a2b7f6e4f7084468996))
* Fix Vue alias for Cypress component testing ([6a71960](https://github.com/empathyco/x/commit/6a71960ffeef4c4b964084c924feac76e25850b5))
* handle dynamic content in empathize (#1492) ([db082ef](https://github.com/empathyco/x/commit/db082efdcfa6fda3863a344f884cd05848bac97d))
* **history-queries:** fix class selector in history queries' e2e test ([af5e83b](https://github.com/empathyco/x/commit/af5e83bd789d81b6f20e38a3555cf6502e784b42)), closes [EX-1857](https://searchbroker.atlassian.net/browse/EX-1857)
* **history-queries:** fix history queries removing queries when replacing last stored query ([37e0cd9](https://github.com/empathyco/x/commit/37e0cd9adc8d32ee70326c5ec1f20438ed83493c)), closes [EX-1764](https://searchbroker.atlassian.net/browse/EX-1764)
* **history-queries:** fixed toggle related tag action to clean the previous related tags ([9be7469](https://github.com/empathyco/x/commit/9be7469787154350b88bda51636e2215751f9527)), closes [EX-2213](https://searchbroker.atlassian.net/browse/EX-2213)
* **history-queries:** legacy history queries stored in the browser without selected filters (#1333) ([96608f8](https://github.com/empathyco/x/commit/96608f87a0b6c3e6c76b7a919cd085d3c2d6c133))
* **history-queries:** map selected filters correctly when coming from Query Preview (#1325) ([61fdfd1](https://github.com/empathyco/x/commit/61fdfd1f4af0183952084abfd8a72ecdd76ee6ee))
* **history-queries:** replace last query, if the last word of it is refined in the new query ([03ea1e0](https://github.com/empathyco/x/commit/03ea1e0cb8bda5814132ef63d83437d81e5c5376)), closes [EX-3084](https://searchbroker.atlassian.net/browse/EX-3084)
* identation error in search-box.md ([614407e](https://github.com/empathyco/x/commit/614407e17a4f198e9c8ad11ca324a00ee7275fa6))
* **identifier-results:** Fix default plugin config. (#296) ([68d4b93](https://github.com/empathyco/x/commit/68d4b93f3f8d439814a11055ac657c0bce5accfd)), closes [EX-5247](https://searchbroker.atlassian.net/browse/EX-5247) [EX-5247](https://searchbroker.atlassian.net/browse/EX-5247)
* **identifier-results:** fix the request action to save the results if the query is empty ([761beca](https://github.com/empathyco/x/commit/761beca702d6243c7f3197566b9e9dfb8e25b330)), closes [EX-2200](https://searchbroker.atlassian.net/browse/EX-2200)
* **identifier-results:** provide resultClickExtraEvents so BaseResultLink emits them when clicked ([da2da47](https://github.com/empathyco/x/commit/da2da47ed1a1fe431dfdfc5a16205967c2ec1f06)), closes [EX-4980](https://searchbroker.atlassian.net/browse/EX-4980)
* include tokens in deprecated theme css file (#1202) ([298163e](https://github.com/empathyco/x/commit/298163e722022efe5af59aa9fb08eb245584ffe1))
* **index.html:** added link to polyfill.io to load polyfills necessary for running the project in IE ([08be43a](https://github.com/empathyco/x/commit/08be43a5fde7dd13e82e86c412a9236287f18119)), closes [EX-2707](https://searchbroker.atlassian.net/browse/EX-2707)
* **infinite-scroll:** getting xBus from XPlugin instead useXBus ([b936ae5](https://github.com/empathyco/x/commit/b936ae585b4ef5ae390515cfc2c3a0dfc782ad39))
* **jenkins:** add test command for Jenkins CI ([d04b3a6](https://github.com/empathyco/x/commit/d04b3a67367954392b8c82b4087812e7c6e34444)), closes [EX-1702](https://searchbroker.atlassian.net/browse/EX-1702)
* **jenkinsfile:** Updated Docker image version ([b043019](https://github.com/empathyco/x/commit/b0430190594620dd9e760fe6e3c6206b1727a264))
* **jest:** fix testMatch option to look into src instead all project ([4a46407](https://github.com/empathyco/x/commit/4a4640709502642169c90c372942ea20128e79c1)), closes [EX-1802](https://searchbroker.atlassian.net/browse/EX-1802)
* keyboard navigation within shadow dom (#1571) ([1784c4c](https://github.com/empathyco/x/commit/1784c4cb6f130947a2454f5adbabcaf4821f8ab2))
* **layout:** avoid shared CSS classes between layouts with scoped (#1605) ([b3cc3f5](https://github.com/empathyco/x/commit/b3cc3f528f71b0877a406c65cadfbecda7aca756))
* **list-components:** fix list components, migrate infinite-scroll directive and deprecated layouts (#1576) ([4b57f19](https://github.com/empathyco/x/commit/4b57f19be601220a4dc6874dc1d5efa8fdbcf991))
* **main-scroll:** obtain observed container element reliably to work with any Vue version (#1552) ([0b4e415](https://github.com/empathyco/x/commit/0b4e41504409dd35a3da0fcf35fa471ea8350f6f))
* make `appear` attribute configurable on animations that have it set to `true` by default (#862) ([7e2cd52](https://github.com/empathyco/x/commit/7e2cd52933385fcee4a7944fd474d2314ac3291d)), closes [EX-5970](https://searchbroker.atlassian.net/browse/EX-5970)
* Make `Home` grid next queries use grid data rather than state data. (#687) ([e340ed0](https://github.com/empathyco/x/commit/e340ed0c4fc4d70a0912c38296812c2fcc0c4e23)), closes [EX-6955](https://searchbroker.atlassian.net/browse/EX-6955)
* make arrays reactive with ref in useHybridInject (#1437) ([75e6fbf](https://github.com/empathyco/x/commit/75e6fbf0b5c2cc95a2bb6f5549afed5eeca635ca))
* make promoted and banner position optional (#817) ([a2a8d5d](https://github.com/empathyco/x/commit/a2a8d5dcc03451e046d00f87f3545dfd46c050c5)), closes [EX-7333](https://searchbroker.atlassian.net/browse/EX-7333)
* **modal:** set focusOnOpen for the main-modal to false (#1074) ([655e8eb](https://github.com/empathyco/x/commit/655e8eb6bc5bedab6b79ab2a7c7d6110f9d27437)), closes [EX-7710](https://searchbroker.atlassian.net/browse/EX-7710)
* move the display-results-provider to fix semantics sliding panel (#1317) ([018d2c5](https://github.com/empathyco/x/commit/018d2c59620deda073dfbe12c04cafe8b5ecd349))
* **next-queries:** avoid clearing next-queries when the query is empty ([e147b40](https://github.com/empathyco/x/commit/e147b40f54f3ccba333f1177b4767768f2bc23d2)), closes [EX-1880](https://searchbroker.atlassian.net/browse/EX-1880)
* **platform-adapter:** change semantics url path (#1230) ([b8210b5](https://github.com/empathyco/x/commit/b8210b59960474a3ad86ffe1a9ee6bc35567ea6e))
* **plugin:** fix the types to allow overriding parts of the store ([80b7eae](https://github.com/empathyco/x/commit/80b7eae6fb81b3765ba571b96ea923d57c4c5f76)), closes [EX-2803](https://searchbroker.atlassian.net/browse/EX-2803)
* **popular-searches:** fix popular searches and query suggestions canceling requests. ([818c373](https://github.com/empathyco/x/commit/818c373acc0036b2f20378ebdcba2c261890d03b)), closes [EX-4697](https://searchbroker.atlassian.net/browse/EX-4697)
* prevent flickering animation on query preview list second load ([e7141a3](https://github.com/empathyco/x/commit/e7141a3941284896bd9a341b8a81bfdfa07515c5))
* prevent node-ipc vulnerability ([fc8b83c](https://github.com/empathyco/x/commit/fc8b83ce73bdbd7148ce99ad3a95d7a7658bd8ba))
* prevent snippet-config-extra-params of firing change event with no changes (#1393) ([73a7a1b](https://github.com/empathyco/x/commit/73a7a1b4168fbcbca23b665baf45fd0e7398f494))
* **promoted:** fix name export of PromotedsList component ([e29bc52](https://github.com/empathyco/x/commit/e29bc52d0c82ba85dc013882e5d80674a870de2f)), closes [EX-4484](https://searchbroker.atlassian.net/browse/EX-4484)
* **query-preview-list:** enable inherit attrs (#1458) ([1adbfe0](https://github.com/empathyco/x/commit/1adbfe04665e289aa0c325daced40f257669fe2d))
* **query-suggestions:** fix missing css class, slots docs, slot naming to kebab case and binds ([24a0e8d](https://github.com/empathyco/x/commit/24a0e8dfdcbdfc23ad96f81ed1e3acc33ee6eedf)), closes [EX-1794](https://searchbroker.atlassian.net/browse/EX-1794)
* **query-suggestion:** use getter of normalizedQuery to use as query in the component ([d5d7c7a](https://github.com/empathyco/x/commit/d5d7c7aca31e5f8b1f2a57db4be4d67b908f4af3)), closes [EX-1886](https://searchbroker.atlassian.net/browse/EX-1886)
* **queryPreviewList:** repeated query loading issue (#1566) ([60aa0c0](https://github.com/empathyco/x/commit/60aa0c0975eabc3a282cfece4ab64fd29c02a3cb))
* **related-tags:** clear selected related tags when user changes extra params ([b2d9b94](https://github.com/empathyco/x/commit/b2d9b94053aebbbda41659dbc3e4602931fd1bb5)), closes [EX-5188](https://searchbroker.atlassian.net/browse/EX-5188)
* **related-tags:** related tags are now kept when navigating back ([db9f875](https://github.com/empathyco/x/commit/db9f87560000bca05ad3fe06fc449e170c3b9d08)), closes [EX-6131](https://searchbroker.atlassian.net/browse/EX-6131)
* **related-tags:** use `query` instead of `tag` as `key` to ensure unique values (#792) ([53e86bd](https://github.com/empathyco/x/commit/53e86bd43137a9e4cd389f58e0efce8bcf63632c)), closes [EX-7236](https://searchbroker.atlassian.net/browse/EX-7236)
* Remove `@empathyco/x-platform-adapter` dependency from library code. (#575) ([104c7e1](https://github.com/empathyco/x/commit/104c7e10855a67b2adfa68d42d82431f9194ee15)), closes [EX-6437](https://searchbroker.atlassian.net/browse/EX-6437)
* remove `resize-observer-browser` types from tsconfig (#833) ([ce46b2c](https://github.com/empathyco/x/commit/ce46b2cefba5b727679c81862542e367a903b4b0)), closes [EX-7373](https://searchbroker.atlassian.net/browse/EX-7373)
* remove warning when the event is not defined (#918) ([7f70e25](https://github.com/empathyco/x/commit/7f70e257bae41ba34f72c1c580c79862448faea9)), closes [EX-7617](https://searchbroker.atlassian.net/browse/EX-7617)
* **request-getters:** avoid constructing a request when the query is empty or has spaces ([d05b2da](https://github.com/empathyco/x/commit/d05b2da9cfda357c46b904a4f7a8314754987081)), closes [EX-1881](https://searchbroker.atlassian.net/browse/EX-1881)
* restore sliding panel state after a search (#1259) ([c61f3ed](https://github.com/empathyco/x/commit/c61f3edaeb0138d759b583901fad89651bdfaefb))
* **runbooks-integration:** fix the bug on the sidebar paths doesn't match the real paths ([51bcfe2](https://github.com/empathyco/x/commit/51bcfe2e1a687ba7844f4a2d7bc89eb420025159))
* **rxjs:** fix rxjs imports to support rollup commonjs plugin ([e7b3cc4](https://github.com/empathyco/x/commit/e7b3cc4cdea01e9b70889869d84237e7a8f13b24)), closes [EX-1884](https://searchbroker.atlassian.net/browse/EX-1884)
* **search-input:** fix debounced query not cancelled on clear query issue ([aa51554](https://github.com/empathyco/x/commit/aa51554d8192e2ee4fa85a5785fa85b6f6ee5e9c)), closes [EX-2709](https://searchbroker.atlassian.net/browse/EX-2709)
* **search:** batch state reset calls after a search.request parameter changes (#283) ([492e856](https://github.com/empathyco/x/commit/492e8566913428426459ada29ca4963730cfcd7c)), closes [EX-5057](https://searchbroker.atlassian.net/browse/EX-5057)
* **search:** clean sort value after accept a new query ([0e49049](https://github.com/empathyco/x/commit/0e490499c35ac56705a05c12b05be4f5a86ae8ce)), closes [EX-4188](https://searchbroker.atlassian.net/browse/EX-4188)
* **search:** export `SortPickerList` (#1157) ([eaf877d](https://github.com/empathyco/x/commit/eaf877db49b7c6578ce4daf707d91c711621eae2))
* **search:** fix infinite scroll issues when filtering ([24b8640](https://github.com/empathyco/x/commit/24b864068590262830efb689018ba3e8e2675622)), closes [EX-4033](https://searchbroker.atlassian.net/browse/EX-4033)
* **search:** ignore page from url when going to a different query (#1244) ([311c5f8](https://github.com/empathyco/x/commit/311c5f871c279a7cb2dc03daf382ac14da4b23a6))
* **search:** next page is now requested if it has less than the page size results. (#284) ([f574792](https://github.com/empathyco/x/commit/f5747923f60f81564ebf124d95cae8a5d92400d4)), closes [EX-5194](https://searchbroker.atlassian.net/browse/EX-5194)
* **search:** Redirection didn't cancel when a related tag was clicked (#1255) ([b9ff0dc](https://github.com/empathyco/x/commit/b9ff0dce2d41c040f8d3cc8a49f28cf5caa5a558))
* **search:** replace results state to append new results instead of pushing them (#1597) ([e64e3cb](https://github.com/empathyco/x/commit/e64e3cb9f3c046d1c30249fb56b0b3ad32f97925))
* **search:** reset `query`, `page` and `sort` on clear query (#1045) ([5dc0603](https://github.com/empathyco/x/commit/5dc060304980f5c373cd1aa8aebd4d3932723a35)), closes [EX-7663](https://searchbroker.atlassian.net/browse/EX-7663)
* **search:** rows and start parameters calculations moved from getter to action to avoid multiple requests ([84752ba](https://github.com/empathyco/x/commit/84752ba3eb1ab728b6adf5cc62ea31646f42b959)), closes [EX-5047](https://searchbroker.atlassian.net/browse/EX-5047)
* **semantic-queries:** cancel track no results query on QueryPreviewUnmounted event (#1507) ([cc6518e](https://github.com/empathyco/x/commit/cc6518efe8e00bf02240ca54e39ef77d05a3139f))
* send origin in query tagging (#1585) ([92efdf7](https://github.com/empathyco/x/commit/92efdf71a4f794d58b9f68cf68783ca0489eb7ee))
* set query in facets module from selecting a query preview (#1318) ([5868a24](https://github.com/empathyco/x/commit/5868a24e73017bd4173fe0e842bf4de853f758bb))
* **spatial-navigation:** filter out focusable elements if they can't be focused ([84c5c9e](https://github.com/empathyco/x/commit/84c5c9e8c45b72ca4876e6995ca3a26708bd3a60)), closes [EX-1924](https://searchbroker.atlassian.net/browse/EX-1924)
* **storage-service:** add dummy local storage service for node environment ([e3aa865](https://github.com/empathyco/x/commit/e3aa8650c351adbd4ce77e70cdc35c917a85ca4a))
* **tagging:** fix e2e test when a display result has no queryTagging (#1416) ([6193307](https://github.com/empathyco/x/commit/6193307e609ab340fcd5f1f047d87b352c571e72))
* **tagging:** now removing the session clears the session from the storage ([9328aad](https://github.com/empathyco/x/commit/9328aadca920825bdaddeb565ee47ef0430f25fd)), closes [EX-5074](https://searchbroker.atlassian.net/browse/EX-5074)
* **tests-fix:** fix tests making them wait until Vue updates reactive dependencies ([4e937a7](https://github.com/empathyco/x/commit/4e937a7716dde474b489317456187f8a7eab8e56)), closes [EX-1697](https://searchbroker.atlassian.net/browse/EX-1697)
* **tests:** enable new scenario in querySuggestions and fix `isInQuerySuggestions` method ([eb4e3fe](https://github.com/empathyco/x/commit/eb4e3fe21c8489744bfb6d61e01838b662c58d28)), closes [EX-3307](https://searchbroker.atlassian.net/browse/EX-3307)
* **tests:** unable to add breakpoints in vue components (#460) ([5d58b9b](https://github.com/empathyco/x/commit/5d58b9b637ad47606651db2415502cf082d5a15b)), closes [EX-5325](https://searchbroker.atlassian.net/browse/EX-5325)
* type empathize events and replace UserPressedEnter with UserPressedEnterKey ([98055c4](https://github.com/empathyco/x/commit/98055c44e165b06013e63c9829fd363f5e50c87a))
* **types:** fix store generic type constraint for Mutations and Actions ([ab19584](https://github.com/empathyco/x/commit/ab195848b4e90d7235c8deaaef4ce844502d73f5)), closes [EX-1631](https://searchbroker.atlassian.net/browse/EX-1631)
* **url:** a `query` is required to store params in the `URL` ([b105da3](https://github.com/empathyco/x/commit/b105da33b35aaa1e3796790d0ec88c74caf856e5)), closes [EX-6134](https://searchbroker.atlassian.net/browse/EX-6134)
* **url:** default `extra params` are now properly restored ([5540929](https://github.com/empathyco/x/commit/554092985a394e1d2b6087b1129282993da7e8c6)), closes [EX-5203](https://searchbroker.atlassian.net/browse/EX-5203)
* **url:** Fix URL clear query issue ([57680ad](https://github.com/empathyco/x/commit/57680ada60c2d0748f09d029831718ec04660d81)), closes [EX-4949](https://searchbroker.atlassian.net/browse/EX-4949)
* use `cypress run` for headless testing (#1357) ([bc88050](https://github.com/empathyco/x/commit/bc88050a6c525e65d8b0e2d1adacf5d823df9137))
* **vue-styleguidist:** create a props template to overwrite the default styleguidist template ([455a23d](https://github.com/empathyco/x/commit/455a23dfe97debb578c44fe405c4dcaf5bf2f9e5)), closes [EX-1875](https://searchbroker.atlassian.net/browse/EX-1875)
* **vue-styleguidist:** create a vue-docgen slots template to overwrite the default one. Close tags within the documentation between backslashes. ([ce3186e](https://github.com/empathyco/x/commit/ce3186ef1f0d98ebe57d76bc223fef8872e14ae3)), closes [EX-1875](https://searchbroker.atlassian.net/browse/EX-1875)
* **vue3:** fix minor Vue3 warnings about migration (#1533) ([8b65ea7](https://github.com/empathyco/x/commit/8b65ea796c7e02c973ba9566bd6bae17fc879c3e))
* wait for the extra params to make the initial requests (#754) ([468a61b](https://github.com/empathyco/x/commit/468a61b69e11b3917a33d44bd415a5ea14c5c409)), closes [EX-6977](https://searchbroker.atlassian.net/browse/EX-6977)
* watch `props.result.images` directly (#1204) ([4ac9190](https://github.com/empathyco/x/commit/4ac9190754deb34ddd3eed7dc1913230e18a3040))
* **wire-operators:** handle race events for the debounce wire operator ([fa97f8e](https://github.com/empathyco/x/commit/fa97f8e9fdf08d6f2c1be411a0bccea7c93e78ac)), closes [EX-1944](https://searchbroker.atlassian.net/browse/EX-1944)
* **x-module:** deprecate useRegisterXModule composable in favour of register the x-module itself in the import (#1520) ([525b020](https://github.com/empathyco/x/commit/525b020f033b1e44d95e5b4042c8201636c87287))
* **x-plugin.mixin:** refactor $x to get root XComponent inside bus emit ([fdc2c19](https://github.com/empathyco/x/commit/fdc2c1961cde890ee7947071c83dbccf2de472f4)), closes [EX-1698](https://searchbroker.atlassian.net/browse/EX-1698)
* **x-plugin:** fix no results message flash on load ([33f534f](https://github.com/empathyco/x/commit/33f534f0343b4115e9ce4d506a9b3d299277976c)), closes [EX-4951](https://searchbroker.atlassian.net/browse/EX-4951)
* **x-plugin:** improve ResultFeature type values (#1344) ([c4c9f6e](https://github.com/empathyco/x/commit/c4c9f6e69d9f9f2a68619d6f10e918c649b42894))
* **x-plugin:** make immediate emitters async ([ee1d68d](https://github.com/empathyco/x/commit/ee1d68d64b3ad14d7a99241c377bf6c05fa9393f)), closes [EX-1849](https://searchbroker.atlassian.net/browse/EX-1849)


### Performance Improvements

* **e2e:** avoid opening new browser instances to speed up e2e tests ([371fdd7](https://github.com/empathyco/x/commit/371fdd71e98e5d435574192f3ff995916ab66c9e)), closes [EX-3160](https://searchbroker.atlassian.net/browse/EX-3160)


### Styling

* add pre-commit hooks to run eslint and prettier ([3acc741](https://github.com/empathyco/x/commit/3acc7419b6ece4d7f353d0d1240677271a344bae)), closes [EX-4439](https://searchbroker.atlassian.net/browse/EX-4439)
* **base-filter:** reformat code and add style to selected filters ([33b56ac](https://github.com/empathyco/x/commit/33b56acd00b4548758086bc02c3376d967ffce1e)), closes [EX-2712](https://searchbroker.atlassian.net/browse/EX-2712)
* format entire project ([991bd0d](https://github.com/empathyco/x/commit/991bd0d4b9c9467988c61c701d93c37020c558e8)), closes [EX-4287](https://searchbroker.atlassian.net/browse/EX-4287)
* format with prettier and avoid fixing code while linting ([54539a7](https://github.com/empathyco/x/commit/54539a7e4c34bc6a77ab48c4618e14b40be69e16))
* **getters:** rename getters name adding .getter at the end ([b615348](https://github.com/empathyco/x/commit/b6153483760f4d29dc7d1b70e5da26dd45a3d273)), closes [EX-3036](https://searchbroker.atlassian.net/browse/EX-3036)
* **rxjs:** remove rxjs-compat and amend the imports ([d8238e6](https://github.com/empathyco/x/commit/d8238e64daba10c5890bd30d862daa23921a0f97)), closes [EX-2150](https://searchbroker.atlassian.net/browse/EX-2150)
* update prettier and format code (#1026) ([a18cc17](https://github.com/empathyco/x/commit/a18cc172b6638962d53192905cd466f12bccacac)), closes [EX-7877](https://searchbroker.atlassian.net/browse/EX-7877)


* (feat) Implement config utils in the modules with config (#1321) ([393d758](https://github.com/empathyco/x/commit/393d7588d19e01d7b012b8a6b92f01babb080f3e))
*  feat(design-system): Re-do aspect ratio logic with modern `aspect-ratio` property ([7fae9dc](https://github.com/empathyco/x/commit/7fae9dcab71ec8a945f70aa706cce1cb57b4ddd8)), closes [EX-6463](https://searchbroker.atlassian.net/browse/EX-6463)


### Documentation

* activating ready live-examples ([953e6c2](https://github.com/empathyco/x/commit/953e6c2ead73cd464fbb861bcc917134eac478a1)), closes [EX-5705](https://searchbroker.atlassian.net/browse/EX-5705)
* add `queriesPreview` to archetype integration (#735) ([57c719a](https://github.com/empathyco/x/commit/57c719a55208e149c9382483df02ac84cac33259)), closes [EX-6613](https://searchbroker.atlassian.net/browse/EX-6613)
* add guide for integrating X Interface into an existing website ([9e14a52](https://github.com/empathyco/x/commit/9e14a52389c77deede822643e50b34e5bbf78ddf)), closes [EX-5143](https://searchbroker.atlassian.net/browse/EX-5143)
* add local storage info and data purposes ([c1b0b05](https://github.com/empathyco/x/commit/c1b0b05cd9260227cb0689283ff27f34a2b01e51)), closes [EX-4123](https://searchbroker.atlassian.net/browse/EX-4123)
* Add module type to integration script docs (#592) ([907bda8](https://github.com/empathyco/x/commit/907bda8b4d825c93461089691f284c1758624a89))
* add new static docs. ([8a40986](https://github.com/empathyco/x/commit/8a409865fea2cd67e0c2daa5d4464f553ff33a2b)), closes [EX-5033](https://searchbroker.atlassian.net/browse/EX-5033)
* add tests docs in contributing documentation about factory functions and components wrappers ([bac93ee](https://github.com/empathyco/x/commit/bac93ee03fef534f89edac734fc968b2bcb58114)), closes [EX-3760](https://searchbroker.atlassian.net/browse/EX-3760)
* **api-extractor:** add API Extractor to generate the documentation ([8693b07](https://github.com/empathyco/x/commit/8693b07b849b41d94ad5d8a7af143469b3031182)), closes [EX-1558](https://searchbroker.atlassian.net/browse/EX-1558)
* **api-extractor:** add missing api extractor marks ([0312c17](https://github.com/empathyco/x/commit/0312c175d74afcb779b48a491cc9ce4de8bf5250)), closes [EX-1617](https://searchbroker.atlassian.net/browse/EX-1617)
* assets migration (#995) ([04678f1](https://github.com/empathyco/x/commit/04678f104a9e9383af7284d349f26e6c0f5454df))
* avoid creating Methods section in components documentation ([e9c4a65](https://github.com/empathyco/x/commit/e9c4a65bd27360a75902bdad2512e63b2a626c82)), closes [EX-4028](https://searchbroker.atlassian.net/browse/EX-4028)
* bring functional docs from eDocs project (#630) ([27e6dd6](https://github.com/empathyco/x/commit/27e6dd646084983c37fc52894dc95544253405d5)), closes [EX-6237](https://searchbroker.atlassian.net/browse/EX-6237)
* **build:** document how to debug the build process ([a774251](https://github.com/empathyco/x/commit/a7742511112372feb859bd0d504d242aeb4d5e30)), closes [EX-2189](https://searchbroker.atlassian.net/browse/EX-2189)
* change h1 to be h2 ([a7e16c6](https://github.com/empathyco/x/commit/a7e16c616fe2593eccf93799f9a46c688857b35b)), closes [EX-5064](https://searchbroker.atlassian.net/browse/EX-5064)
* **changelog:** fix changelog ([c36dea8](https://github.com/empathyco/x/commit/c36dea8d0b618244f66608be56d998ec9e0ea4bb)), closes [EX-1903](https://searchbroker.atlassian.net/browse/EX-1903)
* clarify how to subscribe to any `XEvent` (#645) ([d57941a](https://github.com/empathyco/x/commit/d57941a52d23f56cb7c04ed49b816a252473243f)), closes [EX-6816](https://searchbroker.atlassian.net/browse/EX-6816)
* **components:** fix column picker vue examples (#1293) ([fa0e817](https://github.com/empathyco/x/commit/fa0e817402261a5e7bddc9af6438ef0b3d1c7448))
* **components:** improve the way to show slot bindings data in the components documentation ([92cb442](https://github.com/empathyco/x/commit/92cb442ac4df40b9f1b0337e2899ddd10e504026)), closes [EX-3832](https://searchbroker.atlassian.net/browse/EX-3832)
* correcting `video-reference` id (#1038) ([bc46163](https://github.com/empathyco/x/commit/bc461638d10ecc9160d3c58bd9c7bfdc26d5df1e))
* **docgen.config:** fix the naming of the md files generated from components ([2fc2eae](https://github.com/empathyco/x/commit/2fc2eae75f3d4ef5da23c4f0755999e1afb96cc8)), closes [EX-1875](https://searchbroker.atlassian.net/browse/EX-1875)
* **docusaurus:** automated sidebar generation & docusaurus markdown headers. ([e94a23f](https://github.com/empathyco/x/commit/e94a23f20f10b6e19dee89916bdde3295d343ded)), closes [EX-2207](https://searchbroker.atlassian.net/browse/EX-2207)
* fix `@empathyco/x-components import path in examples (#1353) ([071f12d](https://github.com/empathyco/x/commit/071f12dd96285a02f56c9ddc52c8fe6b802cefae))
* fix broken link in x-components readme (#561) ([7e3f551](https://github.com/empathyco/x/commit/7e3f551866709299e0f7d2d9e282c890dc2faa21))
* fix components documentation export ([a267e44](https://github.com/empathyco/x/commit/a267e448af5aa657c47aec38b8fe34952663ade8)), closes [EX-3816](https://searchbroker.atlassian.net/browse/EX-3816)
* Fix components documentation markdown ([a9877b5](https://github.com/empathyco/x/commit/a9877b5b64259de2313509290b1254667653b420)), closes [EX-4878](https://searchbroker.atlassian.net/browse/EX-4878)
* fix links and minor typos ([e0197d5](https://github.com/empathyco/x/commit/e0197d5bff978048aed39dff5878d60682b7aa9f)), closes [EX-6125](https://searchbroker.atlassian.net/browse/EX-6125)
* fix links and update repository information and development setup for `x-components` (#394) ([64d2118](https://github.com/empathyco/x/commit/64d2118f95673048df7e1a791ec3ae26da316ec9))
* fix multiple broken links ([226a2e5](https://github.com/empathyco/x/commit/226a2e54a4ed8832c7c47d26254e85c301913d98)), closes [EX-5035](https://searchbroker.atlassian.net/browse/EX-5035)
* fix typo (#1455) ([44eae35](https://github.com/empathyco/x/commit/44eae359b33f9642eb9af02701fd6a3295a2deb9))
* fix typo in UrlHandler docs (#959) ([75e4bbe](https://github.com/empathyco/x/commit/75e4bbe47d4298fccb5d26f6145ac3d203d64b2e))
* **functional:** add my history ui and related docs (#685) ([3a9ac8a](https://github.com/empathyco/x/commit/3a9ac8a769d64196b31f05872fb92ec26dc635ad))
* **functional:** titles refactor and change image source (#790) ([cc177a5](https://github.com/empathyco/x/commit/cc177a5bad6fab363d40140e699e11e0ec6bc53c))
* **history-queries:** fix remove-history-query doc link ([c94f483](https://github.com/empathyco/x/commit/c94f4834c7473cfbb329f93309d057f2a6a767d1)), closes [EX-1778](https://searchbroker.atlassian.net/browse/EX-1778)
* **integration:** add close api function (#1096) ([2602e90](https://github.com/empathyco/x/commit/2602e90cf05eea95707d15ea0dac2a319fee6604))
* **integration:** add getSnippetConfig info (#1387) ([622286b](https://github.com/empathyco/x/commit/622286be7b9e552f3dd1e5563a295c7bd267cc49))
* **integration:** add information about sessionId duration (#1139) ([ef879fc](https://github.com/empathyco/x/commit/ef879fc4df6673cadd5a72d9e62d98f644c4e39f))
* **integration:** how to track add2cart event (#1349) ([65509fd](https://github.com/empathyco/x/commit/65509fdfcbd89ce823bd2a36898c3bbf21b7b3ce))
* **integration:** update integration documentation for query preview with filters (#1336) ([b6d6b70](https://github.com/empathyco/x/commit/b6d6b70a6dff5fa22beac9980026e837aded8f8a))
* optimize images for SEO (#1379) ([b115a08](https://github.com/empathyco/x/commit/b115a08caa450447f0515532c3d9c9fd1125a1a4))
* **query-suggestions:** adapt examples to edocs guidelines ([b2380f9](https://github.com/empathyco/x/commit/b2380f95f85d838f0762ea1e608a3ae65ea11b58)), closes [EX-3490](https://searchbroker.atlassian.net/browse/EX-3490)
* **recommendations:** updated recommendations ui doc (#1249) ([432118a](https://github.com/empathyco/x/commit/432118a2d42e0e0964e2d0e1c0e08b1f5e06bb7b))
* **related-tags:** adapt to eDocs guidelines (#35) ([c0cc8ba](https://github.com/empathyco/x/commit/c0cc8ba8a04ca21a206cecd9e657b354e1ece782))
* **related-tags:** added curation options (#1095) ([ab458c7](https://github.com/empathyco/x/commit/ab458c767fc508f4c1cfd4362589a408a09cfbc9))
* Remove docusaurus headers ([6252165](https://github.com/empathyco/x/commit/62521658374eb5c78112314502606e2d82113a95)), closes [EX-5081](https://searchbroker.atlassian.net/browse/EX-5081)
* remove jsdoc [@links](https://github.com/links) from generated documentation (#1261) ([9082fb2](https://github.com/empathyco/x/commit/9082fb2a9d2be89252cc58931d8b3035849a3123))
* replace enable/disable with activate/deactivate (#1420) ([5370c7c](https://github.com/empathyco/x/commit/5370c7c908db1f78d1b315dfd46a518cb534ca8d))
* review build search UI docs ([fc72ad7](https://github.com/empathyco/x/commit/fc72ad78fbff0deaa2f1a417c8e7f005ea2c8470))
* **search-box:** remove values column in props generated table in component doc ([b04d316](https://github.com/empathyco/x/commit/b04d316b0ed1000e4e31f52b9b3680b4c5e2b539)), closes [EX-4137](https://searchbroker.atlassian.net/browse/EX-4137)
* **search-box:** update ClearSearchInput documentation ([48ed984](https://github.com/empathyco/x/commit/48ed98475490ab8f86f2f5d6d79a809dadb363c2)), closes [EX-4101](https://searchbroker.atlassian.net/browse/EX-4101)
* **search-box:** update props and bindings table style and avoid warning block auto-formatting ([bcd16ce](https://github.com/empathyco/x/commit/bcd16ced1ff058a3f781e0545fa9f62b6eae30e9)), closes [EX-4231](https://searchbroker.atlassian.net/browse/EX-4231)
* **search-button:** update SearchButton documentation ([ca7a7c0](https://github.com/empathyco/x/commit/ca7a7c0b47561bb35452fe9f50f88157bc93db00)), closes [EX-4090](https://searchbroker.atlassian.net/browse/EX-4090)
* **search:** update search input component documentation ([37452ac](https://github.com/empathyco/x/commit/37452ac9e8c734c93fb9ccca54c7ddc218ae905d)), closes [EX-4029](https://searchbroker.atlassian.net/browse/EX-4029)
* **slots:** fix slot and binding documentations for vue styleguidist ([a1855b3](https://github.com/empathyco/x/commit/a1855b3d58bbf33cc4bc1ebcc551ddd847c1e661)), closes [EX-1963](https://searchbroker.atlassian.net/browse/EX-1963)
* **static-docs:** added redirections in static docs metadata (#1341) ([8c1d27f](https://github.com/empathyco/x/commit/8c1d27fdef0ff5b95a274d0693c98495799436bb))
* **titles:** adjusting page, seo, and sidebar titles (#1166) ([510ebc3](https://github.com/empathyco/x/commit/510ebc33eecc667dbecc7e091a8bdfb99b8e71e7))
* update archetype integration and x-adapter docs (#628) ([247899e](https://github.com/empathyco/x/commit/247899e39d4f415f59b8ec1b7376fc72530028c2)), closes [EX-6728](https://searchbroker.atlassian.net/browse/EX-6728)
* Update documentation to differentiate integration from development ([fc8d9fa](https://github.com/empathyco/x/commit/fc8d9faa57faafee90c0f4da159b6040294c099c)), closes [EX-5608](https://searchbroker.atlassian.net/browse/EX-5608)
* update functional docs callout formatting (#671) ([5f1de74](https://github.com/empathyco/x/commit/5f1de74c2e86adb638d692781483cac1ccf70a71))
* use new docs video reference component (#923) ([c1f2bff](https://github.com/empathyco/x/commit/c1f2bffa684c10149c97b4d746fecbe4519fa126))
* **xcomponents:** add documentation about events emitted by components ([9f06570](https://github.com/empathyco/x/commit/9f065702ac9c888e9e8ea386ae8eae18249fd8af)), closes [EX-3465](https://searchbroker.atlassian.net/browse/EX-3465)
* **xcomponents:** move xcomponents documentation to independent file. Added a header to each file ([25b29ca](https://github.com/empathyco/x/commit/25b29ca5f7f45aaa44f5d3925951f04afbbb94c4)), closes [EX-2081](https://searchbroker.atlassian.net/browse/EX-2081)


### Testing

*  E2E tests maintenance (#371) [[EX-5618](https://searchbroker.atlassian.net/browse/EX-5618)] ([e12ca33](https://github.com/empathyco/x/commit/e12ca335235c654f5e1e9ae608950bf527954448))
* add Sort components to Vue 3 migration test (#1454) ([7ccffb0](https://github.com/empathyco/x/commit/7ccffb084cdf6521c57977eca4d19d93f6586a2d))
* **auto-progress-bar:** fix test after Vue3 update (#1582) ([335c370](https://github.com/empathyco/x/commit/335c37021f9a0f6fefaec01714cc31fb6bf66391))
* **base-modal-container:** add e2e test to base-modal-container component ([eba0c67](https://github.com/empathyco/x/commit/eba0c670e5d1c390d8e1109b197aab5d5615b6bd)), closes [EX-1765](https://searchbroker.atlassian.net/browse/EX-1765)
* **component:** configure Cypress component testing ([a39172e](https://github.com/empathyco/x/commit/a39172e030f81abf6f9ad1a0cdd5079ec4320e1b)), closes [EX-4339](https://searchbroker.atlassian.net/browse/EX-4339)
* **components:** fix tests after Vue3 update BATCH 1 ([5d4dec8](https://github.com/empathyco/x/commit/5d4dec81b5b9ee99f1cbfc1d88bbf58cd5188602))
* **default-tests:** Disabled some of old E2E tests ([6fb3c3a](https://github.com/empathyco/x/commit/6fb3c3a16990adeeaaf85df257dd540f8e3558b8)), closes [EX-3088](https://searchbroker.atlassian.net/browse/EX-3088)
* e2e test for base filters search ([5a26129](https://github.com/empathyco/x/commit/5a261293e58401f6f25e9539586790915a062be8)), closes [EX-3232](https://searchbroker.atlassian.net/browse/EX-3232)
* e2e test for column picker list and dropdown ([a76bfec](https://github.com/empathyco/x/commit/a76bfeccaecc624ed2c1fbf5b5150792eb4a23b0)), closes [EX-3219](https://searchbroker.atlassian.net/browse/EX-3219)
* e2e tests for sliding panel component ([a212d4f](https://github.com/empathyco/x/commit/a212d4fac2eed6a37a37279025df337f7d0273d6)), closes [EX-3238](https://searchbroker.atlassian.net/browse/EX-3238)
* **e2e-popular-searches-tests:** add e2e test for popular-searches ([7c43851](https://github.com/empathyco/x/commit/7c4385178a672e843858b26e1d162b4f7ee13b28)), closes [EX-1761](https://searchbroker.atlassian.net/browse/EX-1761)
* **e2e:** adapt `empathize` tests to cucumber ([5d8df38](https://github.com/empathyco/x/commit/5d8df38962023bb2343f3e0c9be863ccf6d54617)), closes [EX-3797](https://searchbroker.atlassian.net/browse/EX-3797)
* **e2e:** add `extra-params` scenarios ([4275c28](https://github.com/empathyco/x/commit/4275c2811ea7b0eaaf588fa4d96a7ae3cf4c43c7)), closes [EX-5377](https://searchbroker.atlassian.net/browse/EX-5377)
* **e2e:** add different possible combinations for filters-search components ([94441e8](https://github.com/empathyco/x/commit/94441e8b29b2f6e5ff8857192cc019fecac4548f)), closes [EX-3601](https://searchbroker.atlassian.net/browse/EX-3601)
* **e2e:** add identifier results tests ([cf0c02a](https://github.com/empathyco/x/commit/cf0c02a601d0688d739b79df6b56e161e96b56b9)), closes [EX-3961](https://searchbroker.atlassian.net/browse/EX-3961)
* **e2e:** Add multiselect-filters test ([5da2401](https://github.com/empathyco/x/commit/5da2401b04c5d6f152e839b59813794c5802d6e8)), closes [EX-3603](https://searchbroker.atlassian.net/browse/EX-3603)
* **e2e:** add new sort tests ([6c077e6](https://github.com/empathyco/x/commit/6c077e6876b92ed13af655d8fba79e0e5c544882)), closes [EX-3666](https://searchbroker.atlassian.net/browse/EX-3666)
* **e2e:** add new sort tests ([45d2ab5](https://github.com/empathyco/x/commit/45d2ab57afb91bf5353a87dd8a71f5958a67d608)), closes [EX-3666](https://searchbroker.atlassian.net/browse/EX-3666)
* **e2e:** add next-queries e2e tests ([02033f2](https://github.com/empathyco/x/commit/02033f29e6d8efbeccc975ea9df5abf0276f3d97)), closes [EX-3047](https://searchbroker.atlassian.net/browse/EX-3047)
* **e2e:** add partial results tests ([d30748c](https://github.com/empathyco/x/commit/d30748cced0afa8b92c8a6c63872c976d773bd50)), closes [EX-3959](https://searchbroker.atlassian.net/browse/EX-3959)
* **e2e:** add templates system ([ada7c78](https://github.com/empathyco/x/commit/ada7c78105f4745059c24808b08ead751b2721c7)), closes [EX-1863](https://searchbroker.atlassian.net/browse/EX-1863)
* **e2e:** add test for base event modal ([ab95f65](https://github.com/empathyco/x/commit/ab95f657e39f75307dd569247dbdc8cfcce087fe)), closes [EX-3228](https://searchbroker.atlassian.net/browse/EX-3228)
* **e2e:** add test for spellcheck component ([a5db182](https://github.com/empathyco/x/commit/a5db1824d73cfeed6d8ae0a8ffeed68f2b2cb477)), closes [EX-3963](https://searchbroker.atlassian.net/browse/EX-3963)
* **e2e:** add tests for `BaseKeyboardNavigation` component ([5c59967](https://github.com/empathyco/x/commit/5c599673d4cf698576b7f45b6d87b132224be62f)), closes [EX-3240](https://searchbroker.atlassian.net/browse/EX-3240)
* **e2e:** add tests scenarios for sort dropdown and list ([1b3a867](https://github.com/empathyco/x/commit/1b3a8677e07017aba8cbbb8137e9afc46462dc95)), closes [EX-3201](https://searchbroker.atlassian.net/browse/EX-3201)
* **e2e:** add typing to e2e stubs ([d218b1b](https://github.com/empathyco/x/commit/d218b1bf4981194aecd9c21606eba01b74472a10))
* **e2e:** column pickers tests refinement ([c8fa2e3](https://github.com/empathyco/x/commit/c8fa2e3556fa5f431c074466e6b2d257c16bb943)), closes [EX-3500](https://searchbroker.atlassian.net/browse/EX-3500)
* **e2e:** complete filter tests scenarios ([cc25bce](https://github.com/empathyco/x/commit/cc25bcec7dd4eadaec9fe67fae564dde5dcecbbf)), closes [EX-3607](https://searchbroker.atlassian.net/browse/EX-3607)
* **e2e:** fix `tagging` using the `mockedAdapter` and replacing `fetch` for `sendBeacon`  ([cf06d2f](https://github.com/empathyco/x/commit/cf06d2f7e9aff3987bc14fa46cd65eace402e612)), closes [EX-5374](https://searchbroker.atlassian.net/browse/EX-5374)
* **e2e:** Fix E2E tests in Firefox ([6d25577](https://github.com/empathyco/x/commit/6d25577ad383e6e82a3072eb22809872dc0dc865)), closes [EX-5525](https://searchbroker.atlassian.net/browse/EX-5525)
* **e2e:** fix imports relative paths issues ([aa24bb3](https://github.com/empathyco/x/commit/aa24bb39012dbae58d45e39e3da443faa01b013b)), closes [EX-3434](https://searchbroker.atlassian.net/browse/EX-3434)
* **e2e:** fix invalid identifier results data test selector ([0c1b780](https://github.com/empathyco/x/commit/0c1b780818ee244d506a603603b2e778e50c34f7))
* **e2e:** fix Keyboard Navigation & Base Modal Container e2e tests ([2679983](https://github.com/empathyco/x/commit/2679983e8367e4e71cf0d4701b6cb49d8f7756e1)), closes [EX-2708](https://searchbroker.atlassian.net/browse/EX-2708)
* **e2e:** fix setting related tags max items to render in sliding panel view ([e3d75c8](https://github.com/empathyco/x/commit/e3d75c8fd4708f80313b22de4da97aa88b07ebb8)), closes [EX-3463](https://searchbroker.atlassian.net/browse/EX-3463)
* **e2e:** fix some e2e tests adding checks as guards ([5640735](https://github.com/empathyco/x/commit/564073523052256c3fab8d51bd544a4725b3737e)), closes [EX-2243](https://searchbroker.atlassian.net/browse/EX-2243)
* **e2e:** fix sort intercepted request ([bfb56a8](https://github.com/empathyco/x/commit/bfb56a8a004fccdde20e4f2342b591e37679201c)), closes [EX-4953](https://searchbroker.atlassian.net/browse/EX-4953)
* **e2e:** fix tagging tests (#270) ([ff2ecba](https://github.com/empathyco/x/commit/ff2ecbac79fd3c16d72a05c133dbe0b60de606f7)), closes [EX-5161](https://searchbroker.atlassian.net/browse/EX-5161)
* **e2e:** implement search-box test scenarios ([438cefa](https://github.com/empathyco/x/commit/438cefabdc82beaadef023058a4976976844e2a4)), closes [EX-2725](https://searchbroker.atlassian.net/browse/EX-2725)
* **e2e:** make `HistoryQueries` test wait for no results (#906) ([82cc3dd](https://github.com/empathyco/x/commit/82cc3ddc0f1339fbff6c04e2eff7dfbf24598672)), closes [EX-7591](https://searchbroker.atlassian.net/browse/EX-7591)
* **e2e:** make `tagging` tests wait for redirection before assertion ([f98cd25](https://github.com/empathyco/x/commit/f98cd254084f60893b1eb723d4081bf0c0f44166)), closes [EX-5273](https://searchbroker.atlassian.net/browse/EX-5273)
* **e2e:** make url tests intercept tracking and wait for each request ([393dbea](https://github.com/empathyco/x/commit/393dbea71648b010a4f3d197c180c91741c6054b)), closes [EX-5127](https://searchbroker.atlassian.net/browse/EX-5127)
* **e2e:** mock adapter for identifier results ([44b0f3a](https://github.com/empathyco/x/commit/44b0f3ac2c8adbcc0d9deedbbdad8a120b51b1cc)), closes [EX-4472](https://searchbroker.atlassian.net/browse/EX-4472)
* **e2e:** mock adapter on next queries requests (#66) ([1434ef7](https://github.com/empathyco/x/commit/1434ef767b305b90522d54ef0cd42d33eea8e38e)), closes [EX-4468](https://searchbroker.atlassian.net/browse/EX-4468)
* **e2e:** mock all the e2e requests of Next Queries (#85) ([cff6438](https://github.com/empathyco/x/commit/cff6438dc3f9053d778ab8b58b789cb37104c3bd))
* **e2e:** mock search-box e2e tests ([155b15c](https://github.com/empathyco/x/commit/155b15c046956fec2ecfbed8bc322360bcad43f0)), closes [EX-4474](https://searchbroker.atlassian.net/browse/EX-4474)
* **e2e:** move stubs creation within the test itself and rewrite mocking features ([f99d4e4](https://github.com/empathyco/x/commit/f99d4e4297dc5e55fbf6b7a3f23dfde4db25d2c6)), closes [EX-4533](https://searchbroker.atlassian.net/browse/EX-4533)
* **e2e:** Reduce command timeout and number of retries. ([5e1521f](https://github.com/empathyco/x/commit/5e1521f53aad1e4bfc8f60c7e705422ab2af052c)), closes [EX-5015](https://searchbroker.atlassian.net/browse/EX-5015)
* **e2e:** refactor test ([00fdd30](https://github.com/empathyco/x/commit/00fdd30dc7ca2315b24404cd80fc17213261baa2)), closes [EX-2110](https://searchbroker.atlassian.net/browse/EX-2110)
* **e2e:** related tags e2e tests ([b16fe9f](https://github.com/empathyco/x/commit/b16fe9f36ebfb0e4a064af4264e6a44a7a124d08)), closes [EX-3155](https://searchbroker.atlassian.net/browse/EX-3155)
* **e2e:** remove sliding panel test wait ([84e54ac](https://github.com/empathyco/x/commit/84e54ac582afb4698ef5451a63f272988b58596d)), closes [EX-5009](https://searchbroker.atlassian.net/browse/EX-5009)
* **e2e:** reorder mocked responses ([8cab691](https://github.com/empathyco/x/commit/8cab691b553af31d9b5bc80130e16886877f1b60)), closes [EX-4923](https://searchbroker.atlassian.net/browse/EX-4923)
* **e2e:** search modal re-opens properly after being closed (#613) ([43282ab](https://github.com/empathyco/x/commit/43282ab1d0ab54af7794c88c89aa8e62326d73d8)), closes [EX-6708](https://searchbroker.atlassian.net/browse/EX-6708)
* **e2e:** stub 'adapter.getTopRecommendations` calls ([93480b4](https://github.com/empathyco/x/commit/93480b4cd14f90b17d85a12debb4a922381b5de7)), closes [EX-3433](https://searchbroker.atlassian.net/browse/EX-3433)
* **e2e:** test for base result image component ([ec00804](https://github.com/empathyco/x/commit/ec00804f42ee6eae371d35737c61ea55cb9b15e9)), closes [EX-1978](https://searchbroker.atlassian.net/browse/EX-1978)
* **e2e:** update `cypress` to version `12.1.0` and replace `cypress-cucumber-preprocessor` with `@badeball/cypress-cucumber-preprocessor` (#747) ([2adb2cd](https://github.com/empathyco/x/commit/2adb2cd03591c37934fb385b120822ef271c359f))
* **e2e:** update Cypress to 7.4.0 ([051f322](https://github.com/empathyco/x/commit/051f3226122a027d41f3e0981c138eb1606e8a2d)), closes [EX-3991](https://searchbroker.atlassian.net/browse/EX-3991)
* **e2e:** updated cypress version ([47df2d7](https://github.com/empathyco/x/commit/47df2d77f2c69e281f211b83a3458c46390a90f8)), closes [EX-2917](https://searchbroker.atlassian.net/browse/EX-2917)
* **e2e:** use main layout in mocked tests ([f98c609](https://github.com/empathyco/x/commit/f98c609cbd32a109e3718538074132e0e1ffa48d)), closes [EX-4750](https://searchbroker.atlassian.net/browse/EX-4750)
* enable e2e test and fix tests (#38) ([9d07a2a](https://github.com/empathyco/x/commit/9d07a2a0d146c5ad9cd5441023b864148759b5b5)), closes [EX-4363](https://searchbroker.atlassian.net/browse/EX-4363)
* **facets-next:** add missing service tests ([7d462e1](https://github.com/empathyco/x/commit/7d462e18847dd0632a66701341078f0a9a1318a3)), closes [EX-4589](https://searchbroker.atlassian.net/browse/EX-4589)
* fix exclude-filters e2e test (#588) ([51ecc52](https://github.com/empathyco/x/commit/51ecc5234b665a2320a760d485bf6da74648f902)), closes [EX-6590](https://searchbroker.atlassian.net/browse/EX-6590)
* fix failing tests (#1241) ([41a1641](https://github.com/empathyco/x/commit/41a1641c591a4387891f359719e3c030339cc40c))
* **history queries:** e2e test history queries ([26a1410](https://github.com/empathyco/x/commit/26a1410a2b6dc037f9daeb458111a93dc24399b4)), closes [EX-2958](https://searchbroker.atlassian.net/browse/EX-2958)
* **keyboard-navigation:** e2e testing for keyboard-navigation ([8b774e8](https://github.com/empathyco/x/commit/8b774e8484607213be62445c2082cfb65c79870d)), closes [EX-1924](https://searchbroker.atlassian.net/browse/EX-1924)
* mock popular searches adapter in e2e tests (#93) ([2a8d652](https://github.com/empathyco/x/commit/2a8d6529c361be7922a2f640affdedd5e830f82e)), closes [EX-4466](https://searchbroker.atlassian.net/browse/EX-4466)
* **next-queries:** add e2e test for next queries ([c060119](https://github.com/empathyco/x/commit/c06011976de6369a587b7b30d13cfea1174221b1)), closes [EX-1840](https://searchbroker.atlassian.net/browse/EX-1840)
* **next-queries:** next queries preview e2e tests (#759) ([adccbf4](https://github.com/empathyco/x/commit/adccbf4a111ac65915b017aca799ac523347ddc1)), closes [EX-6848](https://searchbroker.atlassian.net/browse/EX-6848)
* **no-suggestions:** add e2e tests ([6e6ce50](https://github.com/empathyco/x/commit/6e6ce500b674547a7f2b98197c2d3ea086496307)), closes [EX-1741](https://searchbroker.atlassian.net/browse/EX-1741)
* **partial-results:** mock adapter for partial results e2e tests ([1515e79](https://github.com/empathyco/x/commit/1515e796ab72ada9936cb5d288dea76f83e50bf5)), closes [EX-4647](https://searchbroker.atlassian.net/browse/EX-4647)
* remove old tests ([bbab2ac](https://github.com/empathyco/x/commit/bbab2acf63cab736781d7e171cd3e2389f21621f)), closes [EX-3799](https://searchbroker.atlassian.net/browse/EX-3799)
* Restructure files for non global step def (#382) ([d212692](https://github.com/empathyco/x/commit/d21269273e87e58312fde996fd9be3e5883958b4)), closes [EX-5739](https://searchbroker.atlassian.net/browse/EX-5739) [EX-5739](https://searchbroker.atlassian.net/browse/EX-5739) [EX-5739](https://searchbroker.atlassian.net/browse/EX-5739)
* review skipped tests (#1201) ([8c46a38](https://github.com/empathyco/x/commit/8c46a382dd37f2bf67849d8537c0faa668b430e2))
* **search:** redefine old search tests ([5142bb5](https://github.com/empathyco/x/commit/5142bb5fb61181f199fa1019cf7c910d9736deb8)), closes [EX-3801](https://searchbroker.atlassian.net/browse/EX-3801)
* uncomment tests that were expected to fail (#1405) ([f2310a4](https://github.com/empathyco/x/commit/f2310a43133a1b6e1531d59d8e392912eff96894))
* **vue-jest:** update vue-jest dependency (#1581) ([46ff08b](https://github.com/empathyco/x/commit/46ff08bb5834d790b0c6414fc549141b9a64f1d1))
* **x-plugin:** fix tests to use the installNewXPlugin helper ([82a6a3f](https://github.com/empathyco/x/commit/82a6a3f00a2e461aad148e2d7433c79487a82a5e)), closes [EX-1854](https://searchbroker.atlassian.net/browse/EX-1854)


### Code Refactoring

* add `scoped` attribute to `<style>` to components that were missing it ([a60cf8b](https://github.com/empathyco/x/commit/a60cf8b464a0a8b02c98b831cbd1d8b51645d87e)), closes [EX-3266](https://searchbroker.atlassian.net/browse/EX-3266)
* **animation-factory:** fix Vue3 breaking changes (#1579) ([f915731](https://github.com/empathyco/x/commit/f915731cc8ea662a2066fee054f47885ee2154a9))
* **animations:** rename animations to fit BEM ([d712d09](https://github.com/empathyco/x/commit/d712d09cf73eb12979df97862b51312a0a92d5f0)), closes [EX-3264](https://searchbroker.atlassian.net/browse/EX-3264)
* **base-components:** refactor open and close button components so they're reusable ([7682b28](https://github.com/empathyco/x/commit/7682b2872e0a00db7965d1dac477ec31109ee238)), closes [EX-1894](https://searchbroker.atlassian.net/browse/EX-1894)
* **base-components:** remove pure folder and refactor base components names ([6bbbc44](https://github.com/empathyco/x/commit/6bbbc44fea003f90ceb7387184fa27711552d230)), closes [EX-1793](https://searchbroker.atlassian.net/browse/EX-1793)
* **base-event-button:** migrate base-event-button component to Composition API (#1457) ([39a7a8e](https://github.com/empathyco/x/commit/39a7a8ed4767ae78d447e6ddca530c41f9f681dc))
* **base-result-image:** rename from figure to picture ([55e64de](https://github.com/empathyco/x/commit/55e64de3f44f737225af1028522341915b43fcb9)), closes [EX-2713](https://searchbroker.atlassian.net/browse/EX-2713)
* **base-switch:** decommission of value prop (#1589) ([35968eb](https://github.com/empathyco/x/commit/35968ebb69634984e867b03221d373efe4af96c8))
* **base-switch:** migrate component to vue3 (#1588) ([875a6e2](https://github.com/empathyco/x/commit/875a6e2638885498396db362753550857ec8d7e2))
* **bem-css-classes:** refactor css classes following BEM ([73954e4](https://github.com/empathyco/x/commit/73954e4184781f8330ffea32e4c3a12b66ef5a5d)), closes [EX-1785](https://searchbroker.atlassian.net/browse/EX-1785)
* **bus:** replaced `Subject` with `ReplaySubject` ([ada5ce2](https://github.com/empathyco/x/commit/ada5ce279552e302d1e8ea6a59fde8ee7a8276d4)), closes [EX-1849](https://searchbroker.atlassian.net/browse/EX-1849)
* change to the top of the wiring the ParamsLoadedFromUrl event. ([26634c8](https://github.com/empathyco/x/commit/26634c8010bc4d2e795caceefc622c6329fad72c)), closes [EX-5327](https://searchbroker.atlassian.net/browse/EX-5327)
* **ColumnPickerMixin:** get rid of `ColumnPickerMixin` and refactor components which use it (#1461) ([c5b84da](https://github.com/empathyco/x/commit/c5b84da32b75a37d028e91b64220016a2cfb3037))
* **components/filters:** reorganize components/filters directory ([7c3a2e7](https://github.com/empathyco/x/commit/7c3a2e7a9b35efbed3f9267c41490a5f3f1e50ec)), closes [EX-2911](https://searchbroker.atlassian.net/browse/EX-2911)
* **components:** added default content to some simple components and default style ([b8d1012](https://github.com/empathyco/x/commit/b8d10120fd171aa80e9a33fdf067c7d17e948ff5)), closes [EX-2714](https://searchbroker.atlassian.net/browse/EX-2714)
* **components:** migrate `AutoProgressBar` to `Composition API` (#1087) ([30cfa06](https://github.com/empathyco/x/commit/30cfa06ea5894412ab61db44b876c0645d17913e)), closes [EX-8049](https://searchbroker.atlassian.net/browse/EX-8049)
* **components:** migrate animate-width component to vue 2.7 (#1411) ([47c26fb](https://github.com/empathyco/x/commit/47c26fba64025ae6fc391979e8d82fd366afe5b9))
* **components:** migrate location-provider component to vue 2.7 (#1421) ([98377e8](https://github.com/empathyco/x/commit/98377e8fb4e3a65dce7aa8ddd144cd69f2ab1395))
* **components:** refactor `CollapseFromTop` animation to use only transformations ([3c9be50](https://github.com/empathyco/x/commit/3c9be5090dfb2b554b8efe56150e2f29425c5c2e)), closes [EX-4149](https://searchbroker.atlassian.net/browse/EX-4149)
* **components:** remove warnings first batch (#1575) ([1877da6](https://github.com/empathyco/x/commit/1877da61c2eb5aff5742387dc2285b3db86afda5))
* create alias api composable (#1426) ([6badb3a](https://github.com/empathyco/x/commit/6badb3a9815f880f0f411f948b3755f50e9e60a7))
* **currency-formatter:** extract currency format logic from `base-currency.vue` to a `currency-formatter` utility ([8de1b78](https://github.com/empathyco/x/commit/8de1b78dce319154718f84d12e13f289ce619f32)), closes [EX-2919](https://searchbroker.atlassian.net/browse/EX-2919)
* **decorators:** tidy decorators splitting the bus decorators from the state decorators ([ea37c30](https://github.com/empathyco/x/commit/ea37c30d7e606a353bfd78f8d64f51d8fb66fcb8)), closes [EX-3442](https://searchbroker.atlassian.net/browse/EX-3442)
* **design-system:** Refactor Design System View ([f8faf3b](https://github.com/empathyco/x/commit/f8faf3b049160771fa657ac17be4154f434b558c)), closes [EX-4944](https://searchbroker.atlassian.net/browse/EX-4944)
* **design-system:** rename `styles` folder to `design-system` ([ab7fd0a](https://github.com/empathyco/x/commit/ab7fd0aab86a5f9dd8ed13420032a0e8413afbd4)), closes [EX-4227](https://searchbroker.atlassian.net/browse/EX-4227)
* **design-system:** rename `tokens`  to use `style-dictionary` ([1c25fdc](https://github.com/empathyco/x/commit/1c25fdcbe7e13388e465dabd565597acbda32f85)), closes [EX-4327](https://searchbroker.atlassian.net/browse/EX-4327)
* **directives:** add barrel file in `directives` folder and export them in `src` ([58db0a9](https://github.com/empathyco/x/commit/58db0a9ac61bf78cee4726430deda79860f74015)), closes [EX-3779](https://searchbroker.atlassian.net/browse/EX-3779)
* **e2e:** homogenise and standardise common-steps and test cases ([795e1d9](https://github.com/empathyco/x/commit/795e1d94fac14570505407a33f2887294dc1c260)), closes [EX-3060](https://searchbroker.atlassian.net/browse/EX-3060)
* **exports:** add missing actions and getters exports ([3b17a5a](https://github.com/empathyco/x/commit/3b17a5a95ef677faace3dc6a23b2178f1d8486a3)), closes [EX-2687](https://searchbroker.atlassian.net/browse/EX-2687)
* **extractstate & extractgetters types:** refactor ExtractState and ExtractGetters types ([bda935e](https://github.com/empathyco/x/commit/bda935e87e327688f8fae04a307c15cc0f7a8e6c)), closes [EX-1594](https://searchbroker.atlassian.net/browse/EX-1594)
* **facets:** fix facets performance issues ([e4d0361](https://github.com/empathyco/x/commit/e4d036132761814205ff393bd2b14af8f548ba67)), closes [EX-4800](https://searchbroker.atlassian.net/browse/EX-4800)
* **facets:** move filter components inside the facets module ([89c5a13](https://github.com/empathyco/x/commit/89c5a130e75705896263a947983a9762a456998f)), closes [EX-3270](https://searchbroker.atlassian.net/browse/EX-3270)
* get rid of NoElement component and useNoElementRender composable (#1583) ([059eecc](https://github.com/empathyco/x/commit/059eecc0fd5aa1612c1fc7b4d5ec08cfe5fc5b84))
* **history-queries:** move history queries to the root utils folder ([0d640a1](https://github.com/empathyco/x/commit/0d640a1e21dea92bdffa4162fefd8e350c410301)), closes [EX-1850](https://searchbroker.atlassian.net/browse/EX-1850)
* **history-queries:** refactor removeFromHistory action to accept a `HistoryQuery` instead of an string ([e6f0b5b](https://github.com/empathyco/x/commit/e6f0b5b246be1cc8e4df641b4f0e90a8e6e93488)), closes [EX-1738](https://searchbroker.atlassian.net/browse/EX-1738)
* **history-queries:** rename DeleteHistoryQuery to use keyword `remove` ([a004e0c](https://github.com/empathyco/x/commit/a004e0ca9cdcf044fae41f6243bbb3918f495e57)), closes [EX-1811](https://searchbroker.atlassian.net/browse/EX-1811)
* **keyboard-navigation:** use xBus only (#1502) ([8bb3c60](https://github.com/empathyco/x/commit/8bb3c604f308598a124719345bb4cf15a4d83103))
* migrate `BaseVariableColumnGrid` to Composition API (#1482) ([b7e292a](https://github.com/empathyco/x/commit/b7e292ae55560f557dd7db3cfbceed993c7b318e))
* migrate aside to vue 2.7 and use hybridInject (#1433) ([3c94afc](https://github.com/empathyco/x/commit/3c94afc813e58d6c70943e103f814129a17c7eff))
* migrate cross-fade component to vue 2.7 (#1414) ([7f28d20](https://github.com/empathyco/x/commit/7f28d20f3d644cd69da0914ff7a1f3e2819b2966))
* migrate fade component to vue 2.7 (#1413) ([4a8d016](https://github.com/empathyco/x/commit/4a8d0166f34876c71a77ac5326af0f44e4956e77))
* migrate global-x-bus component (#1429) ([48c8ff5](https://github.com/empathyco/x/commit/48c8ff58f112c7ff11df4568358bde8542f32b0a))
* migrate no-element component to vue 2.7 ([29d6a61](https://github.com/empathyco/x/commit/29d6a613aa5a46a6584fcb99015a5cbd99d43b42))
* migrate preselected filters component (#1422) ([4a38318](https://github.com/empathyco/x/commit/4a383186b5ca669938ffbc230c9c3d02805e866b))
* migrate snippet-callbacks to vue 2.7 (#1431) ([168ff1d](https://github.com/empathyco/x/commit/168ff1db8ac964fd12c307c61756d23d84e6ad76))
* move `NonPrimitive`, `Primitive` and `AnyFunction` types from `x-components` to `x-utils` ([7efe460](https://github.com/empathyco/x/commit/7efe4605303492e2de6f42d844f1c3244e0bcef1)), closes [EX-5792](https://searchbroker.atlassian.net/browse/EX-5792)
* move `object` utils from `x-components` to `x-utils` ([512b350](https://github.com/empathyco/x/commit/512b350da4a3dd73ddbd78a7b2965a1e07735a8e)), closes [EX-5793](https://searchbroker.atlassian.net/browse/EX-5793)
* Move aside to its own component in Home view. (#581) ([5b40994](https://github.com/empathyco/x/commit/5b40994af47c268ed10f06624ac1fdc634523a6d)), closes [EX-6525](https://searchbroker.atlassian.net/browse/EX-6525)
* move DeepPartial type from x-components to x-utils ([a26f0c5](https://github.com/empathyco/x/commit/a26f0c54317f17144b4262c60b0a0dc086883eb9)), closes [EX-5835](https://searchbroker.atlassian.net/browse/EX-5835)
* move flie design-system.md to design-system-deprecated (#1319) ([dcea015](https://github.com/empathyco/x/commit/dcea015abb708916e1057dc47d187f09d352b7db))
* move getRottXComponent to a util (#1410) ([6f93f23](https://github.com/empathyco/x/commit/6f93f238fae6da2db7251eb8b2524e306e415814))
* **next-queries:** move actions to an independent folder ([265988f](https://github.com/empathyco/x/commit/265988fa1a415d274408310d82a6494a6c5db03d)), closes [EX-1836](https://searchbroker.atlassian.net/browse/EX-1836)
* **next-queries:** move getters to an independent folder ([e8c6286](https://github.com/empathyco/x/commit/e8c62868542b62ded589d0c10bcd20bb00acabbc)), closes [EX-1836](https://searchbroker.atlassian.net/browse/EX-1836)
* **next-queries:** refactor the next-queries x-module that was already created ([373fca4](https://github.com/empathyco/x/commit/373fca421bc6cf61e3ea8bc25791f61c3fd97ce2)), closes [EX-1729](https://searchbroker.atlassian.net/browse/EX-1729)
* **no-element:** towards getting rid of no-element component (#1564) ([12bb73d](https://github.com/empathyco/x/commit/12bb73dbe7ff6cf761cc2e6581b56e78c9c3359a))
* **noElement:** use the full array of VNodes from the default slot (#1474) ([8fb904c](https://github.com/empathyco/x/commit/8fb904caf9be32ab573bcc9acba4dbc602dd1bc6))
* **plugin:** Rename `inputStatus` to `searchBoxStatus` in Alias API. (#913) ([5cb837e](https://github.com/empathyco/x/commit/5cb837ed57db3fb5543a7f8e82d9beea0088cdd9)), closes [EX-7597](https://searchbroker.atlassian.net/browse/EX-7597)
* **popular-searches:** extract getters from module ([cfdb85a](https://github.com/empathyco/x/commit/cfdb85a2aef0d85a2d2eb37749b4088dea2e2e05)), closes [EX-1789](https://searchbroker.atlassian.net/browse/EX-1789)
* **popular-searches:** extract module actions to an independent files ([572e422](https://github.com/empathyco/x/commit/572e4228294ad5a47f57e865ba66321a24d393d2)), closes [EX-1789](https://searchbroker.atlassian.net/browse/EX-1789)
* **popular-searches:** refactor slot and state names, update docs and refactor variable in test ([fd9cffa](https://github.com/empathyco/x/commit/fd9cffa36f86da4bf8c78aa30b0c1a35619abd82)), closes [EX-1786](https://searchbroker.atlassian.net/browse/EX-1786)
* **query-preview:** migrate query preview component x provide (#1452) ([a60c62a](https://github.com/empathyco/x/commit/a60c62a35d7ba3f13e6561583a0af9f5a46c61b2))
* **query-suggestions:** rename term-suggestions to query-suggestions ([8aa7706](https://github.com/empathyco/x/commit/8aa770688988be7995361744ce19fcf7f628ba8b)), closes [EX-1767](https://searchbroker.atlassian.net/browse/EX-1767)
* remove useHybridInject (#1439) ([f3f6c75](https://github.com/empathyco/x/commit/f3f6c75b9860937869eee89249a50a65480054b8))
* **render-function:** clear void calls (#1580) ([7875ff5](https://github.com/empathyco/x/commit/7875ff5b8420ea1ed03edd3fee28a822582b4641))
* **search-input:** refactor to use XOn decorator instead of creating manually subscription ([a0f3bde](https://github.com/empathyco/x/commit/a0f3bde09ed6a97b9918274f1b06045e4f4b4589)), closes [EX-1781](https://searchbroker.atlassian.net/browse/EX-1781)
* Simplify suggestions list slots. (#893) ([fc4ccb9](https://github.com/empathyco/x/commit/fc4ccb97a91b4c2ff7dfd0d7aed9747d7841b4ed)), closes [EX-7469](https://searchbroker.atlassian.net/browse/EX-7469)
* **sort-mixin:** get rid of SortMixin and refactor components which use it (#1448) ([de0a287](https://github.com/empathyco/x/commit/de0a28754d8fefe8c4db6aa7b7cb5d8407016be2))
* **staggered-fade-and-slide:** use Vue native staggered transition (#1578) ([79e136f](https://github.com/empathyco/x/commit/79e136f04b0b75ddea77c464b8f5ea0ed6602eb1))
* **tagging:** change sessionId creation logic from nanoId to UUID (#1398) ([be06367](https://github.com/empathyco/x/commit/be063673bb74559efab5be9bf6f7ec56688c71f9))
* **tests:** update vue-utils-test version and fix test ([b18fa99](https://github.com/empathyco/x/commit/b18fa9943fd549a49bf511fe7e9a6302a811c212))
* **url:** change `updateUrl` action to be a class ([0c668f2](https://github.com/empathyco/x/commit/0c668f29056deb282d10cb1639ed42980afd4f9e)), closes [EX-4827](https://searchbroker.atlassian.net/browse/EX-4827)
* use `NamedModel` generic parameter to better type models ([4255c94](https://github.com/empathyco/x/commit/4255c94c05b497272409fcba745c29cd8b0d870a)), closes [EX-4734](https://searchbroker.atlassian.net/browse/EX-4734)
* use `setQuery` util in the x modules (#1322) ([9749462](https://github.com/empathyco/x/commit/9749462a08308a121cda61a74209789dabad7b46))
* use implicit return ([99dce8d](https://github.com/empathyco/x/commit/99dce8d461c0b966fabca4ef61ced10ab44b20e2))
* use implicit return ([4405835](https://github.com/empathyco/x/commit/440583514bf78eae6b8531d89ef28a22718831ea))
* **use-register-x-module:** get rid of register x-module composable and deprecated the mixin for the same (#1534) ([4dabc84](https://github.com/empathyco/x/commit/4dabc84c67720e4bfca739b685f3fed5d100f693))
* **utils:** add missing exports to barrel ([4de2aa6](https://github.com/empathyco/x/commit/4de2aa6102343d7e9db5de2d0a4236cb9f07dfef)), closes [EX-4182](https://searchbroker.atlassian.net/browse/EX-4182)
* **v-deep:** replace by :deep() (#1577) ([71c08db](https://github.com/empathyco/x/commit/71c08dbc175093bbfc56160e3b07b8774fcbc683))
* **x-plugin:** extract `XComponentAliasAPI` logic to a separate file and improve aliases generation ([b874566](https://github.com/empathyco/x/commit/b874566755ec0220463f77b347760cb67d316e0b)), closes [EX-3189](https://searchbroker.atlassian.net/browse/EX-3189) [EX-3189](https://searchbroker.atlassian.net/browse/EX-3189) [EX-3288](https://searchbroker.atlassian.net/browse/EX-3288) [feature/EX-3189](https://searchbroker.atlassian.net/browse/EX-3189)
* **x-plugin:** extract getters Proxy creation from XPlugin ([000a333](https://github.com/empathyco/x/commit/000a3331ead77a9942a194e8c97d72d242c6d3e0)), closes [EX-1594](https://searchbroker.atlassian.net/browse/EX-1594)
* **x-plugin:** remove global messages object in favour of individual messages ([ae10a9b](https://github.com/empathyco/x/commit/ae10a9b11cf2d821b2275934aad2ca55b5e5d71f)), closes [EX-1842](https://searchbroker.atlassian.net/browse/EX-1842)
* **x-plugin:** remove x-plugin singleton and improve testeability ([8cb317f](https://github.com/empathyco/x/commit/8cb317f3c0cf2fe929f52f9e41b3b8034c5cc039)), closes [EX-1854](https://searchbroker.atlassian.net/browse/EX-1854)
* **xevents:** refactor XEvents into their respective module ([84b2458](https://github.com/empathyco/x/commit/84b2458933ffd0fe8319a5b684d6efeb695c7c84)), closes [EX-1847](https://searchbroker.atlassian.net/browse/EX-1847)


### Build System

* adjust rollup production build for Vue3 (#1603) ([ed587b1](https://github.com/empathyco/x/commit/ed587b16a56b32734e9cf3ff05311954627f3820))
* **browserslist:** add browserslist configuration ([af5bd1d](https://github.com/empathyco/x/commit/af5bd1da25e47db956891cd8cb99d3e82e114b4c)), closes [EX-1561](https://searchbroker.atlassian.net/browse/EX-1561)
* Delete unused `Jenkinsfile`. (#1075) ([fb9a15b](https://github.com/empathyco/x/commit/fb9a15b80686293b3bd14c8129ed045d8a6c99f2))
* **dependencies:** bump `@bahmutov/cypress-esbuild-preprocessor` from `2.1.5` to `2.2.0` (#1082) ([106c2d1](https://github.com/empathyco/x/commit/106c2d1eba6e1d3b03ac75a04bdec3e961579fef))
* **dependencies:** fix Vue & Vuex versions (#686) ([177e851](https://github.com/empathyco/x/commit/177e8511f4458fa13c627210cdfbbf6d42a85b17)), closes [EX-6918](https://searchbroker.atlassian.net/browse/EX-6918)
* **dependencies:** update [@vue-cli](https://github.com/vue-cli) dependencies to 4.5.x ([ceae76a](https://github.com/empathyco/x/commit/ceae76a1d98c7a4c6007eb023ac4c304c4da8205)), closes [EX-3335](https://searchbroker.atlassian.net/browse/EX-3335)
* **dependencies:** update `[@empathy](https://github.com/empathy)` dependencies ([f67a088](https://github.com/empathyco/x/commit/f67a088e32d782ac6db06469389477b34dd0025d)), closes [EX-1903](https://searchbroker.atlassian.net/browse/EX-1903)
* **dependencies:** update `search-adapter` and `search-types` versions ([76f316f](https://github.com/empathyco/x/commit/76f316f110ed7f051f57d1b3dfd4462b79456b5f)), closes [EX-3664](https://searchbroker.atlassian.net/browse/EX-3664)
* **dependencies:** update `search-adapter` version ([06e98e2](https://github.com/empathyco/x/commit/06e98e24f0a9f2d4598a5adc462c135ae7bf5466)), closes [EX-4067](https://searchbroker.atlassian.net/browse/EX-4067)
* **dependencies:** update `typescript` to `4.9.4` and its dependencies to their latest version (#993) ([500ab57](https://github.com/empathyco/x/commit/500ab57e4729f5c4dcefaa31ed4a8497ddd349b9)), closes [EX-7288](https://searchbroker.atlassian.net/browse/EX-7288)
* **dependencies:** update dependencies to match with the rest of the projects ([c9f511a](https://github.com/empathyco/x/commit/c9f511a5694471df266922f48d8d82a117fd2490)), closes [EX-1884](https://searchbroker.atlassian.net/browse/EX-1884)
* **deps:** update `vue` to version `2.7` (#971) ([09fb0fe](https://github.com/empathyco/x/commit/09fb0fe5dbef020565571a4fafc89d2aac544c8e)), closes [EX-7730](https://searchbroker.atlassian.net/browse/EX-7730)
* **deps:** update dependencies ([491f9c5](https://github.com/empathyco/x/commit/491f9c5a27cf5eaa4dc3f31c97ea514bb8f3515b))
* **deps:** update dependencies (#1004) ([7343506](https://github.com/empathyco/x/commit/73435063e97648ed5bb87600bb7cfbb5eb64b70c))
* **deps:** update dependencies (#1024) ([e99425f](https://github.com/empathyco/x/commit/e99425fc315526afe40b1fd536bcfde1fc1af08a))
* **deps:** update dependencies (#908) ([840da52](https://github.com/empathyco/x/commit/840da52dec32e04cf2b402cca2646b49c839e6e8))
* **deps:** update deps (#1046) ([b6957df](https://github.com/empathyco/x/commit/b6957df9d88c0d94c2543047991a63afadd707ff))
* **deps:** update deps (#1062) ([59f29b9](https://github.com/empathyco/x/commit/59f29b9c5861f790a65b061eec628eb35d066b68))
* **deps:** update eslint-plugin dependencies (#447) ([51d60f0](https://github.com/empathyco/x/commit/51d60f0e11fa9667a784bbdb10ba1f39159b382f)), closes [EX-5383](https://searchbroker.atlassian.net/browse/EX-5383)
* **deps:** Upgrade Cypress and Vue Cli plugins versions. (#399) ([630d6b0](https://github.com/empathyco/x/commit/630d6b0d767a3484140ecd252e2be10817e0900d)), closes [EX-5417](https://searchbroker.atlassian.net/browse/EX-5417)
* **design-system:** add the Rollup configuration to build the CSS files of the Design System ([65275fe](https://github.com/empathyco/x/commit/65275fefce1aca014da699dcfd5b041334204a24)), closes [EX-3691](https://searchbroker.atlassian.net/browse/EX-3691)
* Fix colors.js dependency issue ([2ffcc22](https://github.com/empathyco/x/commit/2ffcc222f5666d7866c8d7cd3a0eec7c0bb1f938)), closes [EX-5293](https://searchbroker.atlassian.net/browse/EX-5293)
* fix publish directory ([1745464](https://github.com/empathyco/x/commit/1745464fa2b8f911cfc2a1c0f27717df2eed8b07))
* improve process deleting the temporally directories ([b1fcc66](https://github.com/empathyco/x/commit/b1fcc667930afa7ab11579190dd74e9e57f4c4c0)), closes [EX-2124](https://searchbroker.atlassian.net/browse/EX-2124)
* Load PostCSS plugins from rollup build (#272) ([aaed2f3](https://github.com/empathyco/x/commit/aaed2f328b0b7252853922703283c77bcd1221d0)), closes [EX-5162](https://searchbroker.atlassian.net/browse/EX-5162)
* **package.json:** update fixed dependencies (package-lock.json) and fix eslint version to minor ([114b90c](https://github.com/empathyco/x/commit/114b90cd03aa245e7f97d02aeef5731277395763)), closes [EX-3744](https://searchbroker.atlassian.net/browse/EX-3744)
* remove `polyfills` support ([a06fcf3](https://github.com/empathyco/x/commit/a06fcf333b06a4d26c32304127f02125d101a0fd)), closes [EX-3559](https://searchbroker.atlassian.net/browse/EX-3559)
* Support SSR with createInjectorSSR for styles. (#674) ([85473c3](https://github.com/empathyco/x/commit/85473c31f5aa755890bef4d20f787ba1453b8843)), closes [EX-6892](https://searchbroker.atlassian.net/browse/EX-6892)
* sync duplicated dependencies (#567) ([912e968](https://github.com/empathyco/x/commit/912e9687851594871b3296a5fb26129327939d96)), closes [EX-6412](https://searchbroker.atlassian.net/browse/EX-6412)
* update jest dependencies ([f3fee15](https://github.com/empathyco/x/commit/f3fee157d724292f5cbb7166908d48ef2fb4fe8c)), closes [EX-5027](https://searchbroker.atlassian.net/browse/EX-5027)
* Update TypeScript to 4.3.5.Update TSLib to 2.3.5. ([4cebdfc](https://github.com/empathyco/x/commit/4cebdfc11e1520552a687def3eda1bf0c132e031)), closes [EX-4435](https://searchbroker.atlassian.net/browse/EX-4435)
* upgrade x-translations dependencies ([6e538fa](https://github.com/empathyco/x/commit/6e538facd2a9655532f797e340572550347dfc72)), closes [EX-4506](https://searchbroker.atlassian.net/browse/EX-4506)
* use 2 different versions of search-types ([5a6ac76](https://github.com/empathyco/x/commit/5a6ac76fea26c0f284904d4f514a1370b7c6184b)), closes [EX-4477](https://searchbroker.atlassian.net/browse/EX-4477)


### Continuous Integration

* add token to checkout action (#1511) ([c7cd70a](https://github.com/empathyco/x/commit/c7cd70a5b6df5701b5e46b4558b82485bc40f953))
* export webpack config from `x-archetype-utils` (#760) ([0d7bfa2](https://github.com/empathyco/x/commit/0d7bfa2a63b5aaa3b220a0338fcefdaedc888f32)), closes [EX-7222](https://searchbroker.atlassian.net/browse/EX-7222)
* fix package version and remove `persist-credentials` (#1513) ([c3add80](https://github.com/empathyco/x/commit/c3add8033ac5515e715e1ffff636b6df8133bccc))
* Fix publishing in x-components. Normalize build scripts. (#46) ([c3c2f85](https://github.com/empathyco/x/commit/c3c2f8519c0de1b164074e87e68e77ad1af0d702)), closes [EX-4413](https://searchbroker.atlassian.net/browse/EX-4413)
* **linter:** fix linter issues to pass the CI (#1606) ([aff3151](https://github.com/empathyco/x/commit/aff3151818c64885d7c28e69f511d33ae41b38f5))
* make Cypress cache depend on package. Make eslint cache restore last version if no exact match. ([2498972](https://github.com/empathyco/x/commit/24989726d8e5c6c3450b344fbbc623a3f7246b53)), closes [EX-7721](https://searchbroker.atlassian.net/browse/EX-7721)
* migrate from `npm` & `lerna bootstrap` to `pnpm` (#1047) ([aaaba4f](https://github.com/empathyco/x/commit/aaaba4f8a5498c16e17ea6daf9c18a1f49918f70)), closes [EX-7891](https://searchbroker.atlassian.net/browse/EX-7891)
* **package.json:** configure E2E tests command for CI Jenkins integration ([13fd89f](https://github.com/empathyco/x/commit/13fd89fee73b6c3a5a280af8e123a4721979f549)), closes [EX-1723](https://searchbroker.atlassian.net/browse/EX-1723)
* parallelize steps (#1174) ([3013595](https://github.com/empathyco/x/commit/3013595857c8dac33f36b2c0d08e747b0735c6a0))
* refactor `lint` command to benefit from `nx parallelisation` (#1051) ([1af1503](https://github.com/empathyco/x/commit/1af1503ff118d6232fdbb27e203037a89b1b52e0)), closes [EX-7926](https://searchbroker.atlassian.net/browse/EX-7926)
* release alpha version on every push to main branch ([f86e0b3](https://github.com/empathyco/x/commit/f86e0b3ad14e7a9bd6d659219fe12f6d94ebdb94)), closes [EX-5263](https://searchbroker.atlassian.net/browse/EX-5263)
* silent jest and eslint warnings (#749) ([1413677](https://github.com/empathyco/x/commit/14136776e6a616e21ecd4585a071cdee1569d1cb))
* update `runners` version (#740) ([38f246c](https://github.com/empathyco/x/commit/38f246c306dac40c4afbcdea08336052981ca9b8))
* update package-lock ([528a88c](https://github.com/empathyco/x/commit/528a88c498ef99c05b420a35e76fb525a7033cb0)), closes [EX-4046](https://searchbroker.atlassian.net/browse/EX-4046)
* update rollup and plugins version ([d240f3d](https://github.com/empathyco/x/commit/d240f3de8bc3e226d0bd8ac2d9bd4282cc660b86)), closes [EX-5342](https://searchbroker.atlassian.net/browse/EX-5342)
* use cypress GitHub action (#1198) ([d432a9b](https://github.com/empathyco/x/commit/d432a9b515a2e42ff8feef9a8dd57565a81633e9))
* use matrix steps and jest projects (#919) ([dec53f5](https://github.com/empathyco/x/commit/dec53f5da572a4a5f3c8519222c1ed94ed981967))


### Others

* bump x-components version ([e021f59](https://github.com/empathyco/x/commit/e021f59d294f1a06e8581eb6cd30208d5fc692f8))
* **deps:** update node to 18 (#1196) ([e0e6b35](https://github.com/empathyco/x/commit/e0e6b35eefb3ef83f22e341f662475b0e6066e94))
* **deps:** update node to v18 (#1175) ([14e64e1](https://github.com/empathyco/x/commit/14e64e11fdf7f3d27d59baf56b027857df9e61e7))



## [5.0.0-alpha.81](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.80...@empathyco/x-components@5.0.0-alpha.81) (2024-08-20)


### Features

* **querySuggestions:** hide suggestions that match with any session query (#1600) ([2f51375](https://github.com/empathyco/x/commit/2f51375e04d46e2aba77f08332797285829ebde7))



## [5.0.0-alpha.80](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.79...@empathyco/x-components@5.0.0-alpha.80) (2024-08-19)

**Note:** Version bump only for package @empathyco/x-components





## [5.0.0-alpha.79](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.78...@empathyco/x-components@5.0.0-alpha.79) (2024-08-14)


### Features

* update result information in the QPs (#1591) ([3e99d0c](https://github.com/empathyco/x/commit/3e99d0cdcb25366af2adff977e25d58d45f7421f))



## [5.0.0-alpha.78](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.77...@empathyco/x-components@5.0.0-alpha.78) (2024-08-13)


### Features

* **main-modal:** make events configurable via props (#1590) ([60d630c](https://github.com/empathyco/x/commit/60d630ca2a181d2919b9f1019abbf1eee5dd2c30))



## [5.0.0-alpha.77](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.76...@empathyco/x-components@5.0.0-alpha.77) (2024-08-13)

**Note:** Version bump only for package @empathyco/x-components





## [5.0.0-alpha.76](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.75...@empathyco/x-components@5.0.0-alpha.76) (2024-08-08)


### Bug Fixes

* send origin in query tagging (#1585) ([92efdf7](https://github.com/empathyco/x/commit/92efdf71a4f794d58b9f68cf68783ca0489eb7ee))



## [5.0.0-alpha.75](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.74...@empathyco/x-components@5.0.0-alpha.75) (2024-07-23)


### Code Refactoring

* **no-element:** towards getting rid of no-element component (#1564) ([12bb73d](https://github.com/empathyco/x/commit/12bb73dbe7ff6cf761cc2e6581b56e78c9c3359a))



## [5.0.0-alpha.74](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.73...@empathyco/x-components@5.0.0-alpha.74) (2024-07-23)


### Features

* **display-emitter:** support Vue3 to the component (#1555) ([21bcd52](https://github.com/empathyco/x/commit/21bcd5228bf2cc3e8f31d49fe55683788438e089))



## [5.0.0-alpha.73](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.72...@empathyco/x-components@5.0.0-alpha.73) (2024-07-18)


### Bug Fixes

* keyboard navigation within shadow dom (#1571) ([1784c4c](https://github.com/empathyco/x/commit/1784c4cb6f130947a2454f5adbabcaf4821f8ab2))



## [5.0.0-alpha.72](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.71...@empathyco/x-components@5.0.0-alpha.72) (2024-07-18)


### Bug Fixes

* **queryPreviewList:** repeated query loading issue (#1566) ([60aa0c0](https://github.com/empathyco/x/commit/60aa0c0975eabc3a282cfece4ab64fd29c02a3cb))



## [5.0.0-alpha.71](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.70...@empathyco/x-components@5.0.0-alpha.71) (2024-07-15)

**Note:** Version bump only for package @empathyco/x-components





## [5.0.0-alpha.70](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.69...@empathyco/x-components@5.0.0-alpha.70) (2024-07-11)


### Features

* migrate internal view components (#1563) ([df0d026](https://github.com/empathyco/x/commit/df0d02634d1193f35918a5c8fd6913faa65c9ab7))



## [5.0.0-alpha.69](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.68...@empathyco/x-components@5.0.0-alpha.69) (2024-07-11)


### Features

* migrate Scroll and ScrolToTop componentes (#1562) ([c8182f4](https://github.com/empathyco/x/commit/c8182f4a4435e1e62e7eaee518fb6325fe01bf7e))



## [5.0.0-alpha.68](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.67...@empathyco/x-components@5.0.0-alpha.68) (2024-07-10)


### Features

* **create-animation:** migrate to composition API (#1553) ([1097c0d](https://github.com/empathyco/x/commit/1097c0d1b9dd63f9573812b9ddb41b790725b46e))



## [5.0.0-alpha.67](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.66...@empathyco/x-components@5.0.0-alpha.67) (2024-07-10)


### Features

* migrate url-handler x-module (#1556) ([9445758](https://github.com/empathyco/x/commit/94457580884be4b03ec72fa18231350bdf3f115a))



## [5.0.0-alpha.66](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.65...@empathyco/x-components@5.0.0-alpha.66) (2024-07-10)


### Features

* **icons:** migrate icons to composition API (#1551) ([243419f](https://github.com/empathyco/x/commit/243419f15b504cea6f8db3ef53899915a174a031))



## [5.0.0-alpha.65](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.64...@empathyco/x-components@5.0.0-alpha.65) (2024-07-09)


### Features

* migrate experience controls (#1530) ([91ee6d0](https://github.com/empathyco/x/commit/91ee6d0f171b870c42e6dcc95229a6be66b7067e))



## [5.0.0-alpha.64](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.63...@empathyco/x-components@5.0.0-alpha.64) (2024-07-09)


### Bug Fixes

* **main-scroll:** obtain observed container element reliably to work with any Vue version (#1552) ([0b4e415](https://github.com/empathyco/x/commit/0b4e41504409dd35a3da0fcf35fa471ea8350f6f))



## [5.0.0-alpha.63](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.62...@empathyco/x-components@5.0.0-alpha.63) (2024-07-08)


### Features

* migrate filters components to Composition API (#1550) ([dd6a2d7](https://github.com/empathyco/x/commit/dd6a2d728632e81c25cc918c1cac1aa10daab590))



## [5.0.0-alpha.62](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.61...@empathyco/x-components@5.0.0-alpha.62) (2024-07-08)


### Features

* **renderless-extra-param:** migrate to composition API (#1546) ([3f111f9](https://github.com/empathyco/x/commit/3f111f98fdf0a4175dce0a5d8711bb8d4e4729df))



## [5.0.0-alpha.61](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.60...@empathyco/x-components@5.0.0-alpha.61) (2024-07-03)


### Features

* **fallback-disclaimer:** migration to composition api (#1545) ([6af6737](https://github.com/empathyco/x/commit/6af6737e854616567822e6ea5a09f093a7368960))



## [5.0.0-alpha.60](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.59...@empathyco/x-components@5.0.0-alpha.60) (2024-07-03)


### Features

* migrate device-detector component (#1544) ([4083571](https://github.com/empathyco/x/commit/4083571bd2fdfc268b529c4ea5a02acb81eecc32))



## [5.0.0-alpha.59](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.58...@empathyco/x-components@5.0.0-alpha.59) (2024-07-03)


### Features

* **tagging:** migrate to composition API (#1543) ([f06e35d](https://github.com/empathyco/x/commit/f06e35d25fb561bca1b53f579ed7ace8674b9085))



## [5.0.0-alpha.58](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.57...@empathyco/x-components@5.0.0-alpha.58) (2024-07-02)


### ⚠ BREAKING CHANGES

* **simple-filter:** use cssClasses prop to pass classes through the component in Vue 3 instead of class or :class when using RenderlessFilter or SimpleFilter components

### Features

* **simple-filter:** migrate RenderlessFilter and SimpleFilter to composition API(#1529) ([8d3a2f2](https://github.com/empathyco/x/commit/8d3a2f23748eec700be10f83cad909b6fdf2aa9b))



## [5.0.0-alpha.57](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.56...@empathyco/x-components@5.0.0-alpha.57) (2024-07-01)


### Features

* **facets:** migrate AllFilter component to Composition API (#1535) ([0b00671](https://github.com/empathyco/x/commit/0b006711297f6fb3721622082fe63b87ce4bcbf7))


### Bug Fixes

* **vue3:** fix minor Vue3 warnings about migration (#1533) ([8b65ea7](https://github.com/empathyco/x/commit/8b65ea796c7e02c973ba9566bd6bae17fc879c3e))



## [5.0.0-alpha.56](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.55...@empathyco/x-components@5.0.0-alpha.56) (2024-07-01)


### Features

* migrate `Redirection` component to composition api (#1532) ([93c0809](https://github.com/empathyco/x/commit/93c08094a33f9828631ad4e4bbb9ac7831db5963))



## [5.0.0-alpha.55](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.54...@empathyco/x-components@5.0.0-alpha.55) (2024-06-26)


### ⚠ BREAKING CHANGES

* **use-register-x-module:** get rid of useRegisterXModule composable. Use XPlugin.registerXModule(xModule) or InstallXOptions.initialXModules instead

### Code Refactoring

* **use-register-x-module:** get rid of register x-module composable and deprecated the mixin for the same (#1534) ([4dabc84](https://github.com/empathyco/x/commit/4dabc84c67720e4bfca739b685f3fed5d100f693))



## [5.0.0-alpha.54](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.53...@empathyco/x-components@5.0.0-alpha.54) (2024-06-24)


### Features

* replace DisableAnimationMixin by useDisableAnimation composable (#1469) ([f498d3f](https://github.com/empathyco/x/commit/f498d3fba5d294391dcfca47f9724558e98f50f0))



## [5.0.0-alpha.53](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.52...@empathyco/x-components@5.0.0-alpha.53) (2024-06-24)


### Features

* **extra-params:** migrate extra params and snippet config extra params (#1531) ([d869f18](https://github.com/empathyco/x/commit/d869f1886c11f74af8a6350033d7567385ad629d))



## [5.0.0-alpha.52](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.51...@empathyco/x-components@5.0.0-alpha.52) (2024-06-20)


### Features

* migrate `QueryPreviewButton` component to composition API (#1525) ([3eff0c7](https://github.com/empathyco/x/commit/3eff0c7c9479abbebbda59e8cc538af6f55375e1))



## [5.0.0-alpha.51](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.50...@empathyco/x-components@5.0.0-alpha.51) (2024-06-19)


### Features

* migrate popular-searches x-module (#1524) ([f79456d](https://github.com/empathyco/x/commit/f79456d4589b3f9dee5fd86fad9625b853dde267))



## [5.0.0-alpha.50](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.49...@empathyco/x-components@5.0.0-alpha.50) (2024-06-19)


### Features

* migrate `facets provider` component to use Composition API (#1523) ([eff7b8d](https://github.com/empathyco/x/commit/eff7b8d92c54aece07061c2d8ce58507a56e7d01))



## [5.0.0-alpha.49](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.48...@empathyco/x-components@5.0.0-alpha.49) (2024-06-18)


### Features

* migrate `next-queries` module to composition API ([324d5d8](https://github.com/empathyco/x/commit/324d5d866167352b9ad5e1b2858853ce197fe7fe))



## [5.0.0-alpha.48](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.47...@empathyco/x-components@5.0.0-alpha.48) (2024-06-18)


### Features

* migrate `identifier-results` x-module to composition API (#1521) ([81b18d0](https://github.com/empathyco/x/commit/81b18d03b3ae2ba9df05f5c288a7eab0e0e7966c))



## [5.0.0-alpha.47](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.46...@empathyco/x-components@5.0.0-alpha.47) (2024-06-17)


### Bug Fixes

* **x-module:** deprecate useRegisterXModule composable in favour of register the x-module itself in the import (#1520) ([525b020](https://github.com/empathyco/x/commit/525b020f033b1e44d95e5b4042c8201636c87287))



## [5.0.0-alpha.46](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.45...@empathyco/x-components@5.0.0-alpha.46) (2024-06-17)


### Features

* **search:** add the capability to reload the current search (#1515) ([617c3b0](https://github.com/empathyco/x/commit/617c3b0d4c07a1054d95c9b4316b86dc5112643e))



## [5.0.0-alpha.45](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.44...@empathyco/x-components@5.0.0-alpha.45) (2024-06-14)


### Features

* **recommendations:** migrate recommendations x-module to composition api (#1519) ([5d44214](https://github.com/empathyco/x/commit/5d44214092af033d9cbf88ec9f306d15a1ded120))



## [5.0.0-alpha.44](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.43...@empathyco/x-components@5.0.0-alpha.44) (2024-06-14)


### Features

* migrate `Spellcheck` and `SpellcheckButton` components to composition api (#1518) ([0e848a7](https://github.com/empathyco/x/commit/0e848a70d69a780b4a053d5bc78b432178f21327))



## [5.0.0-alpha.43](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.42...@empathyco/x-components@5.0.0-alpha.43) (2024-06-13)


### Features

* migrate semantics queries module to composition api (#1508) ([72914a2](https://github.com/empathyco/x/commit/72914a25195e2e546da343d32c6a4544b38bdd91))



## [5.0.0-alpha.42](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.41...@empathyco/x-components@5.0.0-alpha.42) (2024-06-12)


### Features

* migrate `Banner` and `Promoted` to composition API (#1506) ([c102fd9](https://github.com/empathyco/x/commit/c102fd96b26425df2ed8d73d58b3db8fc454deeb))
* migrate RTs module to composition API (#1498) ([22c5325](https://github.com/empathyco/x/commit/22c5325666441121e8ee64bfaa4c51ddad11939a))



## [5.0.0-alpha.41](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.40...@empathyco/x-components@5.0.0-alpha.41) (2024-06-12)


### Features

* migrate `query suggestions` module to composition api (#1497) ([4a9c742](https://github.com/empathyco/x/commit/4a9c742007476367328be6c978d16ec16ae115c1))



## [5.0.0-alpha.40](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.39...@empathyco/x-components@5.0.0-alpha.40) (2024-06-12)


### Features

* migrate history queries x module to composition api (#1494) ([cd51e9b](https://github.com/empathyco/x/commit/cd51e9bb2afb77bbb8f935445bfda360dcfaafde))



## [5.0.0-alpha.39](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.34...@empathyco/x-components@5.0.0-alpha.39) (2024-06-11)


### Bug Fixes

* **semantic-queries:** cancel track no results query on QueryPreviewUnmounted event (#1507) ([cc6518e](https://github.com/empathyco/x/commit/cc6518efe8e00bf02240ca54e39ef77d05a3139f))


### Continuous Integration

* add token to checkout action (#1511) ([c7cd70a](https://github.com/empathyco/x/commit/c7cd70a5b6df5701b5e46b4558b82485bc40f953))
* fix package version and remove `persist-credentials` (#1513) ([c3add80](https://github.com/empathyco/x/commit/c3add8033ac5515e715e1ffff636b6df8133bccc))



## [5.0.0-alpha.38](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.37...@empathyco/x-components@5.0.0-alpha.38) (2024-06-11)

**Note:** Version bump only for package @empathyco/x-components

## [5.0.0-alpha.37](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.36...@empathyco/x-components@5.0.0-alpha.37) (2024-06-10)

**Note:** Version bump only for package @empathyco/x-components

## [5.0.0-alpha.36](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.35...@empathyco/x-components@5.0.0-alpha.36) (2024-06-10)

**Note:** Version bump only for package @empathyco/x-components

## [5.0.0-alpha.35](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.34...@empathyco/x-components@5.0.0-alpha.35) (2024-06-07)

**Note:** Version bump only for package @empathyco/x-components


## [5.0.0-alpha.34](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.33...@empathyco/x-components@5.0.0-alpha.34) (2024-06-06)

**Note:** Version bump only for package @empathyco/x-components


## [5.0.0-alpha.33](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.32...@empathyco/x-components@5.0.0-alpha.33) (2024-06-05)


### Code Refactoring

* **keyboard-navigation:** use xBus only (#1502) ([8bb3c60](https://github.com/empathyco/x/commit/8bb3c604f308598a124719345bb4cf15a4d83103))



## [5.0.0-alpha.32](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.31...@empathyco/x-components@5.0.0-alpha.32) (2024-06-05)


### Features

* migrate PartialQueryButton and PartialResultsList (#1501) ([5e87123](https://github.com/empathyco/x/commit/5e87123d4a6c1edeb05f83c31ee8f096b5558e0f))



## [5.0.0-alpha.31](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.30...@empathyco/x-components@5.0.0-alpha.31) (2024-06-04)


### Features

* migrate BaseEventsModal to composition API ([7ef04b6](https://github.com/empathyco/x/commit/7ef04b65bcef2eb9b9dc5bc107bc02823831d444))



## [5.0.0-alpha.30](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.29...@empathyco/x-components@5.0.0-alpha.30) (2024-06-04)


### Features

* **base-id-modal:** migrate to composition API (#1500) ([6274c67](https://github.com/empathyco/x/commit/6274c676946536c9c1c4e54205ebda18c79b8f55))



## [5.0.0-alpha.29](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.28...@empathyco/x-components@5.0.0-alpha.29) (2024-05-31)


### Features

* **keyboard-navigation:** migrate keyboard-navigation component to composition API (#1493) ([4cf31c9](https://github.com/empathyco/x/commit/4cf31c9df4b751514deaaef4c9abfe4ee5ddfc40))



## [5.0.0-alpha.28](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.27...@empathyco/x-components@5.0.0-alpha.28) (2024-05-31)


### Features

* **panels:** migrate `base-panels` components to composition api (#1491) ([077ad4d](https://github.com/empathyco/x/commit/077ad4d1bcc1dcf0ae2e16a02f1ac073481a1892))
* **result-images:** migrate result images components to composition API (#1496) ([624fb45](https://github.com/empathyco/x/commit/624fb459e71b3c0905e53ba70c1a3a15f581a0fc))



## [5.0.0-alpha.27](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.26...@empathyco/x-components@5.0.0-alpha.27) (2024-05-30)


### Features

* **highlight:** migrate highlight component to composition API (#1486) ([10dd541](https://github.com/empathyco/x/commit/10dd5417f861d6e1152483abbd510059d2917f48))



## [5.0.0-alpha.26](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.25...@empathyco/x-components@5.0.0-alpha.26) (2024-05-30)


### Bug Fixes

* **animation:** fix Expected Object, got Function on animations props (#1489) ([4467edc](https://github.com/empathyco/x/commit/4467edcb08c8d4f59044209d0f9a800745f6d6af))



## [5.0.0-alpha.25](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.24...@empathyco/x-components@5.0.0-alpha.25) (2024-05-29)


### Features

* migrate base suggestions component to composition API ([34bd833](https://github.com/empathyco/x/commit/34bd833e58f9b5f559df17ec2781e529476cdda8))


### Bug Fixes

* build ([f3b6ea9](https://github.com/empathyco/x/commit/f3b6ea91039dcfb1a2d2a50977b65aec7c5cd4c8))
* fix type of prop ([fbfca6f](https://github.com/empathyco/x/commit/fbfca6f09f3d5145f87b4a2b7f6e4f7084468996))


### Code Refactoring

* use implicit return ([99dce8d](https://github.com/empathyco/x/commit/99dce8d461c0b966fabca4ef61ced10ab44b20e2))
* use implicit return ([4405835](https://github.com/empathyco/x/commit/440583514bf78eae6b8531d89ef28a22718831ea))



## [5.0.0-alpha.24](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.23...@empathyco/x-components@5.0.0-alpha.24) (2024-05-29)


### Bug Fixes

* handle dynamic content in empathize (#1492) ([db082ef](https://github.com/empathyco/x/commit/db082efdcfa6fda3863a344f884cd05848bac97d))



## [5.0.0-alpha.23](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.22...@empathyco/x-components@5.0.0-alpha.23) (2024-05-28)


### Features

* **base-modal:** migrate base-modal component and side effects (#1479) ([610ec16](https://github.com/empathyco/x/commit/610ec16e20b10a344936b2914c61085e22a09dfd))
* **sliding-panel:** migrate sliding-panel component to composition API (#1485) ([bf9e1a3](https://github.com/empathyco/x/commit/bf9e1a38364a23402562a19ce8095452da5f02d7))



## [5.0.0-alpha.22](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.21...@empathyco/x-components@5.0.0-alpha.22) (2024-05-28)


### Code Refactoring

* migrate `BaseVariableColumnGrid` to Composition API (#1482) ([b7e292a](https://github.com/empathyco/x/commit/b7e292ae55560f557dd7db3cfbceed993c7b318e))



## [5.0.0-alpha.21](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.20...@empathyco/x-components@5.0.0-alpha.21) (2024-05-28)


### Features

* replace extra divs with `NoElement` (#1484) ([cc7042e](https://github.com/empathyco/x/commit/cc7042e5f144f2abc9eb39e3834c8a153795f558))



## [5.0.0-alpha.20](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.19...@empathyco/x-components@5.0.0-alpha.20) (2024-05-28)


### Features

* **empathize:** migrate empathize component to composition API (#1481) ([ae34083](https://github.com/empathyco/x/commit/ae34083978ea658f7b740f7a4f701b3dd74c0b2f))



## [5.0.0-alpha.19](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.18...@empathyco/x-components@5.0.0-alpha.19) (2024-05-27)


### Features

* Replace `layoutsmixin` by `useLayouts` composable (#1480) ([71feaae](https://github.com/empathyco/x/commit/71feaae8493fb683919967bdf52de161a4e4fbf2))



## [5.0.0-alpha.18](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.17...@empathyco/x-components@5.0.0-alpha.18) (2024-05-23)


### Features

* **search-box:** migrate search-box x-module components to Composition API (#1476) ([5c2b7bc](https://github.com/empathyco/x/commit/5c2b7bcf47281f9a3bb2ea65a1bfb73c6d850260))



## [5.0.0-alpha.17](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.16...@empathyco/x-components@5.0.0-alpha.17) (2024-05-22)


### Features

* **use-debounce:** create useDebounce composable to deprecate Debounce decorator (#1475) ([67f0e42](https://github.com/empathyco/x/commit/67f0e42079839ec9c0f74a9d25ecf9bb2de9a9ab))



## [5.0.0-alpha.16](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.15...@empathyco/x-components@5.0.0-alpha.16) (2024-05-22)


### Code Refactoring

* **noElement:** use the full array of VNodes from the default slot (#1474) ([8fb904c](https://github.com/empathyco/x/commit/8fb904caf9be32ab573bcc9acba4dbc602dd1bc6))



## [5.0.0-alpha.15](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.14...@empathyco/x-components@5.0.0-alpha.15) (2024-05-21)

**Note:** Version bump only for package @empathyco/x-components





## [5.0.0-alpha.14](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.13...@empathyco/x-components@5.0.0-alpha.14) (2024-05-21)


### Features

* **use-x-bus:** unsubscribe from bus events when component is unmounted (#1472) ([36f542a](https://github.com/empathyco/x/commit/36f542ad255096816fccba4c7dcec8e5a9571550))



## [5.0.0-alpha.13](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.12...@empathyco/x-components@5.0.0-alpha.13) (2024-05-17)


### ⚠ BREAKING CHANGES

* **scroll:** `WindowScroll' component will no longer be available and has been removed.

### Features

* **scroll:** replace `ScrollMixin` by `UseScroll` composable (#1473) ([26244cd](https://github.com/empathyco/x/commit/26244cdc8ced863918f0ceb8138ca89bf6792461))



## [5.0.0-alpha.12](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.11...@empathyco/x-components@5.0.0-alpha.12) (2024-05-15)


### Features

* migrate `FiltersInjection` mixin (#1467) ([839c663](https://github.com/empathyco/x/commit/839c66334c98ed399ce354a2c5a3a842734ed54c))



## [5.0.0-alpha.11](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.10...@empathyco/x-components@5.0.0-alpha.11) (2024-05-13)


### Features

* replace `AnimationsMixin` with `useCollapseAnimation` composable (#1468) ([e3ee9d9](https://github.com/empathyco/x/commit/e3ee9d94f9acc4abdcd1c591a754c86d9a6abbb7))



## [5.0.0-alpha.10](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.9...@empathyco/x-components@5.0.0-alpha.10) (2024-05-09)


### Features

* Replace FacetsMixin by useFacets composable (#1462) ([bb7e0ce](https://github.com/empathyco/x/commit/bb7e0cede8653d82e436db696e80c1bdbcb9cc41))



## [5.0.0-alpha.9](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.8...@empathyco/x-components@5.0.0-alpha.9) (2024-05-09)


### Features

* migrate `ItemsListInjection` mixin (#1460) ([a89fb51](https://github.com/empathyco/x/commit/a89fb5179de040695f13d56f43de50917e1c7f97))



## [5.0.0-alpha.8](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.7...@empathyco/x-components@5.0.0-alpha.8) (2024-05-08)


### ⚠ BREAKING CHANGES

* `MainScroll` drops the usage of `NoElement` as root element and uses a div instead. This extra div could break the style of an application that relies on `MainScroll` rendering their content directly.
`MainScrollItem` drops the usage of `NoElement` if no `tag` prop is passed and uses a div as fallback.

### Features

* migrate `MainScroll` and `MainScrollItem` components (#1456) ([b720132](https://github.com/empathyco/x/commit/b7201322bbf1f5696e80e00622d21d653228177c))



## [5.0.0-alpha.7](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.6...@empathyco/x-components@5.0.0-alpha.7) (2024-05-06)


### ⚠ BREAKING CHANGES

* **ColumnPickerMixin:** `BaseColumnPickerDropdown` component will no longer emit the `change` event, use `update:modelValue` instead.
`BaseColumnPickerDropdown` prop for the selected columns was renamed from `value` to `modelValue`.

`BaseColumnPickerList` component will no longer emit the `change` event, use `update:modelValue` instead.
`BaseColumnPickerList` prop for the selected columns was renamed from `value` to `modelValue`.

`ColumnPickerMixin` has been removed.

### Code Refactoring

* **ColumnPickerMixin:** get rid of `ColumnPickerMixin` and refactor components which use it (#1461) ([c5b84da](https://github.com/empathyco/x/commit/c5b84da32b75a37d028e91b64220016a2cfb3037))



## [5.0.0-alpha.6](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.5...@empathyco/x-components@5.0.0-alpha.6) (2024-05-03)

**Note:** Version bump only for package @empathyco/x-components





## [5.0.0-alpha.5](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.4...@empathyco/x-components@5.0.0-alpha.5) (2024-05-01)


### Testing

* add Sort components to Vue 3 migration test (#1454) ([7ccffb0](https://github.com/empathyco/x/commit/7ccffb084cdf6521c57977eca4d19d93f6586a2d))



## [5.0.0-alpha.4](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.3...@empathyco/x-components@5.0.0-alpha.4) (2024-05-01)


### Bug Fixes

* **query-preview-list:** enable inherit attrs (#1458) ([1adbfe0](https://github.com/empathyco/x/commit/1adbfe04665e289aa0c325daced40f257669fe2d))



## [5.0.0-alpha.3](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.2...@empathyco/x-components@5.0.0-alpha.3) (2024-05-01)


### Code Refactoring

* **base-event-button:** migrate base-event-button component to Composition API (#1457) ([39a7a8e](https://github.com/empathyco/x/commit/39a7a8ed4767ae78d447e6ddca530c41f9f681dc))



## [5.0.0-alpha.2](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.1...@empathyco/x-components@5.0.0-alpha.2) (2024-05-01)


### Documentation

* fix typo (#1455) ([44eae35](https://github.com/empathyco/x/commit/44eae359b33f9642eb9af02701fd6a3295a2deb9))



## [5.0.0-alpha.1](https://github.com/empathyco/x/compare/@empathyco/x-components@5.0.0-alpha.0...@empathyco/x-components@5.0.0-alpha.1) (2024-04-29)


### Code Refactoring

* **query-preview:** migrate query preview component x provide (#1452) ([a60c62a](https://github.com/empathyco/x/commit/a60c62a35d7ba3f13e6561583a0af9f5a46c61b2))



## [5.0.0-alpha.0](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.46...@empathyco/x-components@5.0.0-alpha.0) (2024-04-24)


### ⚠ BREAKING CHANGES

* **sort-mixin:** base-dropdown component will no longer emit the `change` event, use `update:modelValue` instead.
base-dropdown prop for the selected item was renamed from `value` to `modelValue`.

### Code Refactoring

* **sort-mixin:** get rid of SortMixin and refactor components which use it (#1448) ([de0a287](https://github.com/empathyco/x/commit/de0a28754d8fefe8c4db6aa7b7cb5d8407016be2))



## [4.1.0-alpha.46](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.45...@empathyco/x-components@4.1.0-alpha.46) (2024-04-22)


### Features

* export pageLoaderButton component (#1449) ([115f744](https://github.com/empathyco/x/commit/115f7448fc92cee5be4151191d4b1a347fd570a1))



## [4.1.0-alpha.45](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.44...@empathyco/x-components@4.1.0-alpha.45) (2024-04-19)


### Features

* **bus:** make `useXBus` get bus from `XPlugin` (#1447) ([c57d1af](https://github.com/empathyco/x/commit/c57d1aff8df162e5b99b78822ba5013b617d4aba))



## [4.1.0-alpha.44](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.43...@empathyco/x-components@4.1.0-alpha.44) (2024-04-19)


### Features

* EMP-3849 Create vue3-migration-test package ([399fe51](https://github.com/empathyco/x/commit/399fe5176b8c0a5206ed7da4edf9c54c1219f70b))


### Bug Fixes

* Fix @vue/compat alias for x-components imports ([d6d7e2f](https://github.com/empathyco/x/commit/d6d7e2f26e6944af7453c213b8d0a1d28ff359eb))
* Fix Vue alias for Cypress component testing ([6a71960](https://github.com/empathyco/x/commit/6a71960ffeef4c4b964084c924feac76e25850b5))



## [4.1.0-alpha.43](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.42...@empathyco/x-components@4.1.0-alpha.43) (2024-04-08)


### Features

* migrate result variant provider (#1440) ([b981d9b](https://github.com/empathyco/x/commit/b981d9ba35394288957e13adbffbaaded142e6c7))



## [4.1.0-alpha.42](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.41...@empathyco/x-components@4.1.0-alpha.42) (2024-04-08)


### Features

* migrate result variants selector component (#1438) ([1e6d681](https://github.com/empathyco/x/commit/1e6d681d7368ca04810df5d8d6116e702face4ff))



## [4.1.0-alpha.41](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.40...@empathyco/x-components@4.1.0-alpha.41) (2024-04-08)


### Features

* migrate base-grid component to vue 2.7 (#1441) ([1974715](https://github.com/empathyco/x/commit/19747154d727bec6cbee171df7d655c34f714db0))



## [4.1.0-alpha.40](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.39...@empathyco/x-components@4.1.0-alpha.40) (2024-04-04)


### Code Refactoring

* remove useHybridInject (#1439) ([f3f6c75](https://github.com/empathyco/x/commit/f3f6c75b9860937869eee89249a50a65480054b8))



## [4.1.0-alpha.39](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.38...@empathyco/x-components@4.1.0-alpha.39) (2024-04-04)


### Features

* modify use-$x composable (#1434) ([cd9a0d1](https://github.com/empathyco/x/commit/cd9a0d1acc95e9b79142aa1abe4b5df5d04aef40))



## [4.1.0-alpha.38](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.37...@empathyco/x-components@4.1.0-alpha.38) (2024-03-27)


### Bug Fixes

* make arrays reactive with ref in useHybridInject (#1437) ([75e6fbf](https://github.com/empathyco/x/commit/75e6fbf0b5c2cc95a2bb6f5549afed5eeca635ca))



## [4.1.0-alpha.37](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.36...@empathyco/x-components@4.1.0-alpha.37) (2024-03-22)


### Code Refactoring

* migrate aside to vue 2.7 and use hybridInject (#1433) ([3c94afc](https://github.com/empathyco/x/commit/3c94afc813e58d6c70943e103f814129a17c7eff))



## [4.1.0-alpha.36](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.35...@empathyco/x-components@4.1.0-alpha.36) (2024-03-21)


### Bug Fixes

* bus handling of a location ref (#1432) ([b980638](https://github.com/empathyco/x/commit/b98063826f5657088bb613db1a529a446389ed67))



## [4.1.0-alpha.35](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.34...@empathyco/x-components@4.1.0-alpha.35) (2024-03-20)


### Code Refactoring

* create alias api composable (#1426) ([6badb3a](https://github.com/empathyco/x/commit/6badb3a9815f880f0f411f948b3755f50e9e60a7))



## [4.1.0-alpha.34](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.33...@empathyco/x-components@4.1.0-alpha.34) (2024-03-19)


### Code Refactoring

* migrate no-element component to vue 2.7 ([29d6a61](https://github.com/empathyco/x/commit/29d6a613aa5a46a6584fcb99015a5cbd99d43b42))



## [4.1.0-alpha.33](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.32...@empathyco/x-components@4.1.0-alpha.33) (2024-03-19)


### Code Refactoring

* migrate snippet-callbacks to vue 2.7 (#1431) ([168ff1d](https://github.com/empathyco/x/commit/168ff1db8ac964fd12c307c61756d23d84e6ad76))



## [4.1.0-alpha.32](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.31...@empathyco/x-components@4.1.0-alpha.32) (2024-03-13)


### Code Refactoring

* migrate preselected filters component (#1422) ([4a38318](https://github.com/empathyco/x/commit/4a383186b5ca669938ffbc230c9c3d02805e866b))



## [4.1.0-alpha.31](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.30...@empathyco/x-components@4.1.0-alpha.31) (2024-03-13)


### Code Refactoring

* migrate global-x-bus component (#1429) ([48c8ff5](https://github.com/empathyco/x/commit/48c8ff58f112c7ff11df4568358bde8542f32b0a))



## [4.1.0-alpha.30](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.29...@empathyco/x-components@4.1.0-alpha.30) (2024-03-12)


### Features

* send totalHits -1 when there are no results and semantics (#1425) ([d393649](https://github.com/empathyco/x/commit/d39364944d2ee76ee5412480e9c3cdeb55fc4fa1))



## [4.1.0-alpha.29](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.28...@empathyco/x-components@4.1.0-alpha.29) (2024-03-08)


### Features

* create load next page component (#1424) ([cf05167](https://github.com/empathyco/x/commit/cf05167904dfdc018e36f33c7d0df2ff0e5de4a9))



## [4.1.0-alpha.28](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.27...@empathyco/x-components@4.1.0-alpha.28) (2024-03-07)


### Bug Fixes

*  Next Queries not being calculated when using Related Tags (#1428) ([50306b6](https://github.com/empathyco/x/commit/50306b600c681c1bd54e209ee048893295a016cb))



## [4.1.0-alpha.27](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.26...@empathyco/x-components@4.1.0-alpha.27) (2024-03-04)


### Features

* change useHybridInject so it works more like vue inject (#1427) ([f7e2946](https://github.com/empathyco/x/commit/f7e2946771213c06b6b7f6c9b4987ba971303463))



## [4.1.0-alpha.26](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.25...@empathyco/x-components@4.1.0-alpha.26) (2024-02-23)


### Documentation

* replace enable/disable with activate/deactivate (#1420) ([5370c7c](https://github.com/empathyco/x/commit/5370c7c908db1f78d1b315dfd46a518cb534ca8d))



## [4.1.0-alpha.25](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.24...@empathyco/x-components@4.1.0-alpha.25) (2024-02-23)


### Code Refactoring

* **components:** migrate location-provider component to vue 2.7 (#1421) ([98377e8](https://github.com/empathyco/x/commit/98377e8fb4e3a65dce7aa8ddd144cd69f2ab1395))



## [4.1.0-alpha.24](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.23...@empathyco/x-components@4.1.0-alpha.24) (2024-02-21)


### Features

* migrating base-rating component using defineComponent sintax (#1419) ([3fb116a](https://github.com/empathyco/x/commit/3fb116ad5a28addcf53c6d66035072e7013a7818))



## [4.1.0-alpha.23](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.22...@empathyco/x-components@4.1.0-alpha.23) (2024-02-21)

**Note:** Version bump only for package @empathyco/x-components





## [4.1.0-alpha.22](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.21...@empathyco/x-components@4.1.0-alpha.22) (2024-02-21)


### Features

* **filters:** update preselected filters component so it reacts to snippetConfig changes (#1404) ([05983f3](https://github.com/empathyco/x/commit/05983f352830b7d52c2b586566938749fa9ce44e))



## [4.1.0-alpha.21](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.20...@empathyco/x-components@4.1.0-alpha.21) (2024-02-20)


### Features

* migrate base-switch to use defineComponent sintax (#1415) ([0592ec9](https://github.com/empathyco/x/commit/0592ec94f7f47c91946d0e3a465dde134dd12021))



## [4.1.0-alpha.20](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.19...@empathyco/x-components@4.1.0-alpha.20) (2024-02-20)


### Bug Fixes

* **tagging:** fix e2e test when a display result has no queryTagging (#1416) ([6193307](https://github.com/empathyco/x/commit/6193307e609ab340fcd5f1f047d87b352c571e72))



## [4.1.0-alpha.19](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.18...@empathyco/x-components@4.1.0-alpha.19) (2024-02-20)


### Features

* **composables:** create XBus composable (#1412) ([5246135](https://github.com/empathyco/x/commit/5246135aaf2581e338dcf1934aeb8fb781cfe0a0))
* **tagging:** send query event when a result from a QP is clicked (#1409) ([2236948](https://github.com/empathyco/x/commit/22369482f51fc2e9b36c7b8280ad0da3ab5e504d))


### Code Refactoring

* migrate cross-fade component to vue 2.7 (#1414) ([7f28d20](https://github.com/empathyco/x/commit/7f28d20f3d644cd69da0914ff7a1f3e2819b2966))
* migrate fade component to vue 2.7 (#1413) ([4a8d016](https://github.com/empathyco/x/commit/4a8d0166f34876c71a77ac5326af0f44e4956e77))
* move getRottXComponent to a util (#1410) ([6f93f23](https://github.com/empathyco/x/commit/6f93f238fae6da2db7251eb8b2524e306e415814))



## [4.1.0-alpha.18](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.17...@empathyco/x-components@4.1.0-alpha.18) (2024-02-16)


### Code Refactoring

* **components:** migrate animate-width component to vue 2.7 (#1411) ([47c26fb](https://github.com/empathyco/x/commit/47c26fba64025ae6fc391979e8d82fd366afe5b9))



## [4.1.0-alpha.17](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.16...@empathyco/x-components@4.1.0-alpha.17) (2024-02-14)


### Features

* **composables:** create use getter composable (#1407) ([44a1488](https://github.com/empathyco/x/commit/44a148848ab027a624a3a1980ed4a62cb0956dea))



## [4.1.0-alpha.16](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.15...@empathyco/x-components@4.1.0-alpha.16) (2024-02-14)


### Testing

* uncomment tests that were expected to fail (#1405) ([f2310a4](https://github.com/empathyco/x/commit/f2310a43133a1b6e1531d59d8e392912eff96894))



## [4.1.0-alpha.15](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.14...@empathyco/x-components@4.1.0-alpha.15) (2024-02-13)


### Features

* **composables:** create useState composable (#1402) ([435af42](https://github.com/empathyco/x/commit/435af4222a2ed08d44d728a973406c0e1122b862))



## [4.1.0-alpha.14](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.13...@empathyco/x-components@4.1.0-alpha.14) (2024-02-05)


### Features

* **components:** create useStore composable (#1401) ([b4e42b9](https://github.com/empathyco/x/commit/b4e42b95bdee4dcc869908e9505830cc15e975a8))
* creating useRegisterXModule composable (#1399) ([850a741](https://github.com/empathyco/x/commit/850a741f3a144ae79374d85e7e2f6a2f1c502946))


### Code Refactoring

* **tagging:** change sessionId creation logic from nanoId to UUID (#1398) ([be06367](https://github.com/empathyco/x/commit/be063673bb74559efab5be9bf6f7ec56688c71f9))



## [4.1.0-alpha.13](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.12...@empathyco/x-components@4.1.0-alpha.13) (2024-01-25)


### Features

* **queries-preview:** allow queries preview with same query but different filters or params (#1392) ([4c1f63a](https://github.com/empathyco/x/commit/4c1f63aaf4e9fc75d3b8298b2ea41c1fc207940a))



## [4.1.0-alpha.12](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.11...@empathyco/x-components@4.1.0-alpha.12) (2024-01-25)


### Features

* **components:** composable and component to fire callbacks when an element appears on viewport (#1391) ([c463352](https://github.com/empathyco/x/commit/c46335243c74c604e6f8168c158461edff9d4eb5))



## [4.1.0-alpha.11](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.10...@empathyco/x-components@4.1.0-alpha.11) (2024-01-22)


### Bug Fixes

* prevent snippet-config-extra-params of firing change event with no changes (#1393) ([73a7a1b](https://github.com/empathyco/x/commit/73a7a1b4168fbcbca23b665baf45fd0e7398f494))



## [4.1.0-alpha.10](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.9...@empathyco/x-components@4.1.0-alpha.10) (2024-01-17)

**Note:** Version bump only for package @empathyco/x-components





## [4.1.0-alpha.9](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.8...@empathyco/x-components@4.1.0-alpha.9) (2024-01-17)

**Note:** Version bump only for package @empathyco/x-components





## [4.1.0-alpha.8](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.7...@empathyco/x-components@4.1.0-alpha.8) (2024-01-15)


### Features

* **queries-preview:** display tagging from QP request accessible in QP component (#1389) ([27dfec8](https://github.com/empathyco/x/commit/27dfec8dc2725a7c2300e306d82617a2d1de130f))



## [4.1.0-alpha.7](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.6...@empathyco/x-components@4.1.0-alpha.7) (2024-01-12)


### Features

* **search:** handle display tagging from search response (#1388) ([b6b5d86](https://github.com/empathyco/x/commit/b6b5d8657947b8510f9d23530d709e757e5e3ecf))



## [4.1.0-alpha.6](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.5...@empathyco/x-components@4.1.0-alpha.6) (2024-01-11)


### Features

* update to rollup 4 (#1370) ([a5c471b](https://github.com/empathyco/x/commit/a5c471b7d139393b7c2c0dffd88973029f2ced31))



## [4.1.0-alpha.5](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.4...@empathyco/x-components@4.1.0-alpha.5) (2024-01-03)


### Documentation

* **integration:** add getSnippetConfig info (#1387) ([622286b](https://github.com/empathyco/x/commit/622286be7b9e552f3dd1e5563a295c7bd267cc49))



## [4.1.0-alpha.4](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.3...@empathyco/x-components@4.1.0-alpha.4) (2023-12-29)


### Features

* **x-plugin:** add snippet config getter to XAPI (#1378) ([a76e1b7](https://github.com/empathyco/x/commit/a76e1b716b9aa86fc6853bcf4d1bb7aaa9478f4a))



## [4.1.0-alpha.3](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.2...@empathyco/x-components@4.1.0-alpha.3) (2023-12-29)


### Documentation

* optimize images for SEO (#1379) ([b115a08](https://github.com/empathyco/x/commit/b115a08caa450447f0515532c3d9c9fd1125a1a4))



## [4.1.0-alpha.2](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.1...@empathyco/x-components@4.1.0-alpha.2) (2023-12-28)

**Note:** Version bump only for package @empathyco/x-components





## [4.1.0-alpha.1](https://github.com/empathyco/x/compare/@empathyco/x-components@4.1.0-alpha.0...@empathyco/x-components@4.1.0-alpha.1) (2023-12-27)

**Note:** Version bump only for package @empathyco/x-components





## [4.1.0-alpha.0](https://github.com/empathyco/x/compare/@empathyco/x-components@4.0.2-alpha.0...@empathyco/x-components@4.1.0-alpha.0) (2023-12-11)


### Features

* **query-preview:** use cached query-previews (#1360) ([2579ca4](https://github.com/empathyco/x/commit/2579ca42d52c6f6c428b9129d63dc4a0ddb4788c))



## [4.0.2-alpha.0](https://github.com/empathyco/x/compare/@empathyco/x-components@4.0.1...@empathyco/x-components@4.0.2-alpha.0) (2023-11-29)

**Note:** Version bump only for package @empathyco/x-components





## [4.0.1](https://github.com/empathyco/x/compare/@empathyco/x-components@4.0.1-alpha.0...@empathyco/x-components@4.0.1) (2023-11-24)

**Note:** Version bump only for package @empathyco/x-components





## [4.0.1-alpha.0](https://github.com/empathyco/x/compare/@empathyco/x-components@4.0.0-alpha.1...@empathyco/x-components@4.0.1-alpha.0) (2023-11-22)

**Note:** Version bump only for package @empathyco/x-components





## [4.0.0](https://github.com/empathyco/x/compare/@empathyco/x-components@4.0.0-alpha.1...@empathyco/x-components@4.0.0) (2023-11-21)

**Note:** Version bump only for package @empathyco/x-components





## [4.0.0-alpha.1](https://github.com/empathyco/x/compare/@empathyco/x-components@4.0.0-alpha.0...@empathyco/x-components@4.0.0-alpha.1) (2023-11-20)


### Bug Fixes

* use `cypress run` for headless testing (#1357) ([bc88050](https://github.com/empathyco/x/commit/bc88050a6c525e65d8b0e2d1adacf5d823df9137))



## [4.0.0-alpha.0](https://github.com/empathyco/x/compare/@empathyco/x-components@3.1.0-alpha.3...@empathyco/x-components@4.0.0-alpha.0) (2023-11-16)


### ⚠ BREAKING CHANGES

* **components:** remove deprecated origins from (#1344)
* **facets:** The '__unknown-facet__' value for a facetId is deprecated: it has been replaced by the UNKNOWN_FACET_KEY constant, whose value is '__unknown__'.

Co-authored-by: Guillermo Cacheda <cachedacodes@gmail.com>

### Features

* **components:** remove deprecated origins (#1355) ([3d7c981](https://github.com/empathyco/x/commit/3d7c981380bd8af30724780f7810808d563db471))
* **facets:** Unify __unknown__ and __unknown-facet__ in a constant (#1351) ([30585f2](https://github.com/empathyco/x/commit/30585f2d57653aa33c68f748ff10f93202f1887e))



## [3.1.0-alpha.3](https://github.com/empathyco/x/compare/@empathyco/x-components@3.1.0-alpha.2...@empathyco/x-components@3.1.0-alpha.3) (2023-11-13)


### Features

* migrate from `vue-cli` to `vite` (#1350) ([52a3b6e](https://github.com/empathyco/x/commit/52a3b6e7d94587f6934e838a2e68c99af97f7999))



## [3.1.0-alpha.2](https://github.com/empathyco/x/compare/@empathyco/x-components@3.1.0-alpha.1...@empathyco/x-components@3.1.0-alpha.2) (2023-11-13)


### Documentation

* **integration:** how to track add2cart event (#1349) ([65509fd](https://github.com/empathyco/x/commit/65509fdfcbd89ce823bd2a36898c3bbf21b7b3ce))



## [3.1.0-alpha.1](https://github.com/empathyco/x/compare/@empathyco/x-components@3.1.0-alpha.0...@empathyco/x-components@3.1.0-alpha.1) (2023-11-10)


### Documentation

* fix `@empathyco/x-components import path in examples (#1353) ([071f12d](https://github.com/empathyco/x/commit/071f12dd96285a02f56c9ddc52c8fe6b802cefae))



## [3.1.0-alpha.0](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.1-alpha.4...@empathyco/x-components@3.1.0-alpha.0) (2023-11-06)


### Features

* **extra-params:** allow currency to be an extra param as default ([319851d](https://github.com/empathyco/x/commit/319851da07f04a79aae128081c9c45cd7ae1b1e9))



## [3.0.1-alpha.4](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.1-alpha.3...@empathyco/x-components@3.0.1-alpha.4) (2023-10-31)


### Bug Fixes

* **x-plugin:** improve ResultFeature type values (#1344) ([c4c9f6e](https://github.com/empathyco/x/commit/c4c9f6e69d9f9f2a68619d6f10e918c649b42894))



## [3.0.1-alpha.3](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.1-alpha.2...@empathyco/x-components@3.0.1-alpha.3) (2023-10-30)


### Bug Fixes

* identation error in search-box.md ([614407e](https://github.com/empathyco/x/commit/614407e17a4f198e9c8ad11ca324a00ee7275fa6))



## [3.0.1-alpha.2](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.1-alpha.1...@empathyco/x-components@3.0.1-alpha.2) (2023-10-27)


### Documentation

* **static-docs:** added redirections in static docs metadata (#1341) ([8c1d27f](https://github.com/empathyco/x/commit/8c1d27fdef0ff5b95a274d0693c98495799436bb))



## [3.0.1-alpha.1](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.1-alpha.0...@empathyco/x-components@3.0.1-alpha.1) (2023-10-26)


### Bug Fixes

* **history-queries:** map selected filters correctly when coming from Query Preview (#1325) ([61fdfd1](https://github.com/empathyco/x/commit/61fdfd1f4af0183952084abfd8a72ecdd76ee6ee))



## [3.0.1-alpha.0](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.425...@empathyco/x-components@3.0.1-alpha.0) (2023-10-24)

**Note:** Version bump only for package @empathyco/x-components





# Change Log

All notable changes to this project will be documented in this file. See
[Conventional Commits](https://conventionalcommits.org) for commit guidelines.

## [3.0.0](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.424...@empathyco/x-components@3.0.0) (2023-10-23)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.425](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.424...@empathyco/x-components@3.0.0-alpha.425) (2023-10-23)


### Documentation

* **integration:** update integration documentation for query preview with filters [(#1336)](https://github.com/empathyco/x/pull/1336) ([b6d6b70](https://github.com/empathyco/x/commit/b6d6b70a6dff5fa22beac9980026e837aded8f8a))



## [3.0.0-alpha.424](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.423...@empathyco/x-components@3.0.0-alpha.424) (2023-10-23)

### Bug Fixes

- **history-queries:** legacy history queries stored in the browser without selected filters [(#1333)](https://github.com/empathyco/x/pull/1333)

## [3.0.0-alpha.423](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.422...@empathyco/x-components@3.0.0-alpha.423) (2023-10-19)

### Code Refactoring

- use `setQuery` util in the x modules (#1322)

## [3.0.0-alpha.422](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.421...@empathyco/x-components@3.0.0-alpha.422) (2023-10-12)

### Features

- Implement config utils in the modules with config
  [(#1321)](https://github.com/empathyco/x/pull/1321)

### ⚠ BREAKING CHANGES

- setPageSize search module mutation has been replaced by the `setConfig` mutation.
  `setTaggingConfig` tagging module mutation and `setFacetsConfig` facets module mutation have been
  replaced by the `mergeConfig` mutation.

## [3.0.0-alpha.421](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.420...@empathyco/x-components@3.0.0-alpha.421) (2023-10-11)

### Features

- **history-queries:** filters in history queries
  [(#1315)](https://github.com/empathyco/x/pull/1315)

## [3.0.0-alpha.420](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.419...@empathyco/x-components@3.0.0-alpha.420) (2023-10-11)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.419](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.418...@empathyco/x-components@3.0.0-alpha.419) (2023-10-10)

### Features

- **experience-controls:** Create experience controls module tests
  [(#1303)](https://github.com/empathyco/x/pull/1303)

### Bug Fixes

- move the display-results-provider to fix semantics sliding panel
  [(#1317)](https://github.com/empathyco/x/pull/1317)
- set query in facets module from selecting query preview
  [(#1318)](https://github.com/empathyco/x/pull/1318)

### Code Refactoring

- move file `design-system.md` to design-system-deprecated
  [(#1319)](https://github.com/empathyco/x/pull/1319)

## [3.0.0-alpha.418](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.417...@empathyco/x-components@3.0.0-alpha.418) (2023-10-09)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.417](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.416...@empathyco/x-components@3.0.0-alpha.417) (2023-10-05)

### Features

- utils for the mutation of states with config [(#1313)](https://github.com/empathyco/x/pull/1313)

## [3.0.0-alpha.416](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.415...@empathyco/x-components@3.0.0-alpha.416) (2023-10-05)

### Bug Fixes

- exports for experience controls [(#1312)](https://github.com/empathyco/x/pull/1312)

## [3.0.0-alpha.415](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.414...@empathyco/x-components@3.0.0-alpha.415) (2023-10-04)

### Features

- **experience-controls:** experience controls module and adapter
  [(#1307)](https://github.com/empathyco/x/pull/1307)

## [3.0.0-alpha.414](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.413...@empathyco/x-components@3.0.0-alpha.414) (2023-09-22)

### Features

- **queries-preview:** filter query preview [(#1296)](https://github.com/empathyco/x/pull/1296)

### Documentation

- **components:** fix column picker vue examples [(#1293)](https://github.com/empathyco/x/pull/1293)

## [3.0.0-alpha.413](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.412...@empathyco/x-components@3.0.0-alpha.413) (2023-09-20)

### Features

- **queries-preview:** add filters to the query preview request
  [(#1292)](https://github.com/empathyco/x/pull/1292)
- **queries-preview:** use deep equal to compare request
  [(#1291)](https://github.com/empathyco/x/pull/1291)

## [3.0.0-alpha.412](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.411...@empathyco/x-components@3.0.0-alpha.412) (2023-09-18)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.411](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.410...@empathyco/x-components@3.0.0-alpha.411) (2023-09-18)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.410](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.409...@empathyco/x-components@3.0.0-alpha.410) (2023-09-15)

### ⚠ BREAKING CHANGES

- **queries-preview:** the `QueryPreviewList` component `queries` prop has changed name to
  `queriesPreviewInfo` and the type is an array of `QueryPreviewInfo` as instead of an array of
  strings. The QueryPreview component `query` prop has changed name to `queryPreviewInfo` and the
  type is `QueryPreviewInfo` instead of `string`. `QueryPreviewInfo` type is now exported from the
  module.

### Features

- **queries-preview:** query preview components allow adding extra params to the request
  [(#1270)](https://github.com/empathyco/x/pull/1270)

## [3.0.0-alpha.409](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.408...@empathyco/x-components@3.0.0-alpha.409) (2023-09-15)

### Features

- **scroll:** add top offset when automatically scrolling to main-scroll-item
  [(#1277)](https://github.com/empathyco/x/pull/1277)

## [3.0.0-alpha.408](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.407...@empathyco/x-components@3.0.0-alpha.408) (2023-09-12)

### Bug Fixes

- prevent flickering animation on query preview list second load

## [3.0.0-alpha.407](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.406...@empathyco/x-components@3.0.0-alpha.407) (2023-09-07)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.406](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.405...@empathyco/x-components@3.0.0-alpha.406) (2023-08-25)

### Features

- standardise all events links in component docs section
  [(#1265)](https://github.com/empathyco/x/pull/1265)

## [3.0.0-alpha.405](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.404...@empathyco/x-components@3.0.0-alpha.405) (2023-08-25)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.404](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.403...@empathyco/x-components@3.0.0-alpha.404) (2023-08-23)

### Documentation

- remove jsdoc [@links](https://github.com/links) from generated documentation
  [(#1261)](https://github.com/empathyco/x/pull/1261)

## [3.0.0-alpha.403](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.402...@empathyco/x-components@3.0.0-alpha.403) (2023-08-21)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.402](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.401...@empathyco/x-components@3.0.0-alpha.402) (2023-08-17)

### Bug Fixes

- **components:** restore sliding panel state after search
  [(#1259)](https://github.com/empathyco/x/pull/1259)

## [3.0.0-alpha.401](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.400...@empathyco/x-components@3.0.0-alpha.401) (2023-08-16)

### Documentation

- **recommendations:** updated recommendations ui doc
  [(#1249)](https://github.com/empathyco/x/pull/1249)

## [3.0.0-alpha.400](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.399...@empathyco/x-components@3.0.0-alpha.400) (2023-08-02)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.399](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.398...@empathyco/x-components@3.0.0-alpha.399) (2023-07-31)

### Bug Fixes

- fix base rating component [(#1256)](https://github.com/empathyco/x/pull/1256)

## [3.0.0-alpha.398](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.397...@empathyco/x-components@3.0.0-alpha.398) (2023-07-27)

### Bug Fixes

- **search:** Redirection didn't cancel when related tag was clicked
  [(#1255)](https://github.com/empathyco/x/pull/1255)

## [3.0.0-alpha.397](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.396...@empathyco/x-components@3.0.0-alpha.397) (2023-07-27)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.396](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.395...@empathyco/x-components@3.0.0-alpha.396) (2023-07-26)

### Features

- **facets:** improve customization and add prop classes to editable-number-range-filter
  [(#1253)](https://github.com/empathyco/x/pull/1253)

## [3.0.0-alpha.395](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.394...@empathyco/x-components@3.0.0-alpha.395) (2023-07-25)

### Bug Fixes

- **filters:** Editable number range filter should be unique
  [(#1243)](https://github.com/empathyco/x/pull/1243)

## [3.0.0-alpha.394](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.393...@empathyco/x-components@3.0.0-alpha.394) (2023-07-24)

### Features

- **extra-params:** make the snippet-config-extra-params component react to prop changes

## [3.0.0-alpha.393](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.392...@empathyco/x-components@3.0.0-alpha.393) (2023-07-13)

### ⚠ BREAKING CHANGES

- the property 'querySuggestions' in 'x-plugin' now returns the query suggestions that should be
  displayed based on the module's config. new property called 'fullQuerySuggestions' returns all the
  query suggestions in the module

### Features

- add alias for the query suggestions that should be displayed
  [(#1247)](https://github.com/empathyco/x/pull/1247)

## [3.0.0-alpha.392](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.391...@empathyco/x-components@3.0.0-alpha.392) (2023-07-11)

### Bug Fixes

- **search:** ignore page from url when going to different query
  [(#1244)](https://github.com/empathyco/x/pull/1244)

## [3.0.0-alpha.391](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.390...@empathyco/x-components@3.0.0-alpha.391) (2023-06-27)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.390](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.389...@empathyco/x-components@3.0.0-alpha.390) (2023-06-27)

### Testing

- fix failing tests [(#1241)](https://github.com/empathyco/x/pull/1241)

## [3.0.0-alpha.389](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.388...@empathyco/x-components@3.0.0-alpha.389) (2023-06-15)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.388](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.387...@empathyco/x-components@3.0.0-alpha.388) (2023-06-14)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.387](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.386...@empathyco/x-components@3.0.0-alpha.387) (2023-06-14)

### Features

- **queries-preview:** add isAnyQueryLoadedInPreview composable
  [(#1229)](https://github.com/empathyco/x/pull/1229)
- **tagging:** track displayClick properties in result & tagging request
  [(#1225)](https://github.com/empathyco/x/pull/1225)

## [3.0.0-alpha.386](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.385...@empathyco/x-components@3.0.0-alpha.386) (2023-06-12)

### Features

- **queries-preview:** add loaded previews getter
  [(#1227)](https://github.com/empathyco/x/pull/1227)
- **semantic-queries:** add SemanticQuery component
  [(#1226)](https://github.com/empathyco/x/pull/1226)

## [3.0.0-alpha.385](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.384...@empathyco/x-components@3.0.0-alpha.385) (2023-06-09)

### Features

- make `XAPI` init method async [(#1228)](https://github.com/empathyco/x/pull/1228)

## [3.0.0-alpha.384](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.383...@empathyco/x-components@3.0.0-alpha.384) (2023-06-08)

### Testing

- review skipped tests [(#1201)](https://github.com/empathyco/x/pull/1201)

## [3.0.0-alpha.383](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.382...@empathyco/x-components@3.0.0-alpha.383) (2023-06-08)

### Bug Fixes

- **deps:** update dependency @vueuse/core to v10
  [(#1219)](https://github.com/empathyco/x/pull/1219)
- **platform-adapter:** change semantics url path
  [(#1230)](https://github.com/empathyco/x/pull/1230)

## [3.0.0-alpha.382](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.381...@empathyco/x-components@3.0.0-alpha.382) (2023-06-07)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.381](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.380...@empathyco/x-components@3.0.0-alpha.381) (2023-06-06)

### Features

- **semantic-queries:** add maxItemsToRequest config
  [(#1224)](https://github.com/empathyco/x/pull/1224)
- **tagging:** track displayClick [(#1222)](https://github.com/empathyco/x/pull/1222)

## [3.0.0-alpha.380](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.379...@empathyco/x-components@3.0.0-alpha.380) (2023-05-31)

### Features

- **component:** set configuration for base-result-link to ignore tagging of click
  [(#1211)](https://github.com/empathyco/x/pull/1211)

## [3.0.0-alpha.379](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.378...@empathyco/x-components@3.0.0-alpha.379) (2023-05-30)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.378](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.377...@empathyco/x-components@3.0.0-alpha.378) (2023-05-30)

### Features

- **semantic-queries:** add semantic queries module and component
  [(#1213)](https://github.com/empathyco/x/pull/1213)

## [3.0.0-alpha.377](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.376...@empathyco/x-components@3.0.0-alpha.377) (2023-05-30)

### Features

- **platform-adapter:** add semantic queries to platform adapter
  [(#1212)](https://github.com/empathyco/x/pull/1212)

## [3.0.0-alpha.376](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.375...@empathyco/x-components@3.0.0-alpha.376) (2023-05-30)

### Features

- **queries-preview:** make the QueryPreviewRequestUpdated not replaceable
  [(#1203)](https://github.com/empathyco/x/pull/1203)

## [3.0.0-alpha.375](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.374...@empathyco/x-components@3.0.0-alpha.375) (2023-05-24)

### Features

- **tagging:** add new type values to ResultFeature and FeatureLocation
  [(#1209)](https://github.com/empathyco/x/pull/1209)

## [3.0.0-alpha.374](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.373...@empathyco/x-components@3.0.0-alpha.374) (2023-05-24)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.373](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.372...@empathyco/x-components@3.0.0-alpha.373) (2023-05-24)

### Bug Fixes

- watch `props.result.images` directly [(#1204)](https://github.com/empathyco/x/pull/1204)

## [3.0.0-alpha.372](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.371...@empathyco/x-components@3.0.0-alpha.372) (2023-05-22)

### Bug Fixes

- include tokens in deprecated theme css file [(#1202)](https://github.com/empathyco/x/pull/1202)

## [3.0.0-alpha.371](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.370...@empathyco/x-components@3.0.0-alpha.371) (2023-05-18)

### Bug Fixes

- blur related tag when deselected [(#1199)](https://github.com/empathyco/x/pull/1199)

## [3.0.0-alpha.370](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.369...@empathyco/x-components@3.0.0-alpha.370) (2023-05-16)

### Continuous Integration

- use cypress GitHub action [(#1198)](https://github.com/empathyco/x/pull/1198)

## [3.0.0-alpha.369](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.368...@empathyco/x-components@3.0.0-alpha.369) (2023-05-15)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.368](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.367...@empathyco/x-components@3.0.0-alpha.368) (2023-05-11)

### ⚠ BREAKING CHANGES

- **deps:** minimum node version required is 18.

### Others

- **deps:** update node to 18 [(#1196)](https://github.com/empathyco/x/pull/1196)

## [3.0.0-alpha.367](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.366...@empathyco/x-components@3.0.0-alpha.367) (2023-05-11)

### ⚠ BREAKING CHANGES

- **deps:** minimum version required is node v18

### Features

- migrate suggestions and currency components to vue 3 syntax
  [(#1159)](https://github.com/empathyco/x/pull/1159)

### Bug Fixes

- `BaseResultImage` not showing the right size on load
  [(#1176)](https://github.com/empathyco/x/pull/1176)

### Others

- **deps:** update node to v18 [(#1175)](https://github.com/empathyco/x/pull/1175)

### Continuous Integration

- parallelize steps [(#1174)](https://github.com/empathyco/x/pull/1174)

## [3.0.0-alpha.366](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.365...@empathyco/x-components@3.0.0-alpha.366) (2023-05-04)

### Features

- migrate results to vue 3 syntax [(#1145)](https://github.com/empathyco/x/pull/1145)

## [3.0.0-alpha.365](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.364...@empathyco/x-components@3.0.0-alpha.365) (2023-05-03)

### Features

- migrate filters to vue 3 syntax [(#1144)](https://github.com/empathyco/x/pull/1144)
- migrate panels components to vue 3 syntax [(#1150)](https://github.com/empathyco/x/pull/1150)

## [3.0.0-alpha.364](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.363...@empathyco/x-components@3.0.0-alpha.364) (2023-05-03)

### Features

- migrate modals to vue 3 syntax [(#1141)](https://github.com/empathyco/x/pull/1141)

## [3.0.0-alpha.363](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.362...@empathyco/x-components@3.0.0-alpha.363) (2023-05-03)

### Features

- Adapt Result mapping according to new API standard
  [(#1039)](https://github.com/empathyco/x/pull/1039)

## [3.0.0-alpha.362](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.361...@empathyco/x-components@3.0.0-alpha.362) (2023-05-02)

### Features

- **search:** add dynamic title prop to promoted and banner component
  [(#1168)](https://github.com/empathyco/x/pull/1168)

### Documentation

- **titles:** adjusting page, seo, and sidebar titles
  [(#1166)](https://github.com/empathyco/x/pull/1166)

## [3.0.0-alpha.361](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.360...@empathyco/x-components@3.0.0-alpha.361) (2023-04-26)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.360](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.359...@empathyco/x-components@3.0.0-alpha.360) (2023-04-24)

### ⚠ BREAKING CHANGES

- **design-system:** The `x-components` design system has been deprecated. The exported theme is no
  longer available. If you need support for the old design system you should import
  `@empathyco/x-components/design-system/deprecated-full-theme.css`.
- **design-system:** `x-grid-list` and `x-grid-list__item` classes have been removed from `BaseGrid`
  component.
- **design-system:** `x-grid-list--cols-{columns}` has been renamed to `x-base-grid--cols-{columns}`
- **design-system:** `x-list` class has been removed from the following components:

  `BaseModal`, `BaseSuggetions`, `BaseTabsPanel`, `Facets`, `FiltersList`, `FiltersSearch`,
  `IdentifierResults`, `MyHistory`, `PartialResultList`, `ResultVariantSelector`, `Recommendations`,
  `RelatedTags`, `SlidingPanel`, `SelectedFiltersList`.

- **design-system:** `FixedHeaderAndAsidesLayout` `MultiColumnMaxWidthLayout` and
  `SingleColumnLayout` have been deprecated.
- **design-system:** `BaseModal` default opacity has changed from `0.7` to `0.3`.
- **design-system:** `x-list__item` class has been removed from `BaseTabsPanel` component.
- **design-system:** `x-message` class has been removed from `Redirection` component.

### Features

- **design-system:** deprecate old DS [(#1138)](https://github.com/empathyco/x/pull/1138)

## [3.0.0-alpha.359](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.358...@empathyco/x-components@3.0.0-alpha.359) (2023-04-24)

### Bug Fixes

- **search:** export `SortPickerList` [(#1157)](https://github.com/empathyco/x/pull/1157)

## [3.0.0-alpha.358](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.357...@empathyco/x-components@3.0.0-alpha.358) (2023-04-24)

### Features

- **search:** add sort picker list component [(#1155)](https://github.com/empathyco/x/pull/1155)

## [3.0.0-alpha.357](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.356...@empathyco/x-components@3.0.0-alpha.357) (2023-04-20)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.356](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.355...@empathyco/x-components@3.0.0-alpha.356) (2023-04-20)

### Features

- export sticky modifier [(#1151)](https://github.com/empathyco/x/pull/1151)

## [3.0.0-alpha.355](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.354...@empathyco/x-components@3.0.0-alpha.355) (2023-04-19)

### ⚠ BREAKING CHANGES

- **design-system:** Old `design-system` `progress-bar` styles are now located in the
  `deprecated-full-theme.css` file.
- **design-system:** Renamed `x-progress-bar__line` class to `x-progress-bar-fill`.

### Features

- **design-system:** add XDS progress bar component
  [(#1149)](https://github.com/empathyco/x/pull/1149)

## [3.0.0-alpha.354](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.353...@empathyco/x-components@3.0.0-alpha.354) (2023-04-19)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.353](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.352...@empathyco/x-components@3.0.0-alpha.353) (2023-04-19)

### Features

- **search:** add fallback disclaimer component [(#1122)](https://github.com/empathyco/x/pull/1122)
- **facets:** add dynamic prop to show more/less buttons in sliced-filters
  [(#1146)](https://github.com/empathyco/x/pull/1146)

## [3.0.0-alpha.352](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.351...@empathyco/x-components@3.0.0-alpha.352) (2023-04-18)

### Documentation

- **integration:** add information about sessionId duration
  [(#1139)](https://github.com/empathyco/x/pull/1139)

## [3.0.0-alpha.351](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.350...@empathyco/x-components@3.0.0-alpha.351) (2023-04-17)

### Features

- add `filterItemClass` prop to `HierarchicalFilter`
  [(#1135)](https://github.com/empathyco/x/pull/1135)

## [3.0.0-alpha.350](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.349...@empathyco/x-components@3.0.0-alpha.350) (2023-04-17)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.349](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.348...@empathyco/x-components@3.0.0-alpha.349) (2023-04-13)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.348](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.347...@empathyco/x-components@3.0.0-alpha.348) (2023-04-13)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.347](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.346...@empathyco/x-components@3.0.0-alpha.347) (2023-04-12)

### Features

- **design-system:** deprecate old DS filters [(#1121)](https://github.com/empathyco/x/pull/1121)

## [3.0.0-alpha.346](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.345...@empathyco/x-components@3.0.0-alpha.346) (2023-04-12)

### Features

- **facets:** implement strategy to decide what filters are sent in the request
  [(#1124)](https://github.com/empathyco/x/pull/1124)

## [3.0.0-alpha.345](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.344...@empathyco/x-components@3.0.0-alpha.345) (2023-04-10)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.344](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.343...@empathyco/x-components@3.0.0-alpha.344) (2023-04-10)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.343](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.342...@empathyco/x-components@3.0.0-alpha.343) (2023-03-31)

### Features

- add sticky filters [(#1113)](https://github.com/empathyco/x/pull/1113)

## [3.0.0-alpha.342](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.341...@empathyco/x-components@3.0.0-alpha.342) (2023-03-30)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.341](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.340...@empathyco/x-components@3.0.0-alpha.341) (2023-03-30)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.340](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.339...@empathyco/x-components@3.0.0-alpha.340) (2023-03-29)

### Features

- Minor improvements. [(#1109)](https://github.com/empathyco/x/pull/1109)

## [3.0.0-alpha.339](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.338...@empathyco/x-components@3.0.0-alpha.339) (2023-03-27)

### ⚠ BREAKING CHANGES

- `base-column-picker-list` structure changes. It now wraps the buttons in div instead of using ul
  and li. Additionally, the class for the selected option has been changed to `x-selected`.

### Features

- adapt `base-column-picker-list` to use the XDS component of button group
  [(#1115)](https://github.com/empathyco/x/pull/1115)

## [3.0.0-alpha.338](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.337...@empathyco/x-components@3.0.0-alpha.338) (2023-03-23)

### Features

- **components:** add `columns` prop in `BaseVariableColumnGrid`
  [(#1112)](https://github.com/empathyco/x/pull/1112)

## [3.0.0-alpha.337](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.336...@empathyco/x-components@3.0.0-alpha.337) (2023-03-22)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.336](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.335...@empathyco/x-components@3.0.0-alpha.336) (2023-03-20)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.335](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.334...@empathyco/x-components@3.0.0-alpha.335) (2023-03-16)

### ⚠ BREAKING CHANGES

- **design-system:** Old `design-system` `Tag` styles are now located in the
  `deprecated-full-theme.css` file.
- **design-system:** Old `x-tag--is-curated` and `x-tag--is-selected` classes are no longer used by
  `RelatedTag` component.

### Features

- **design-system:** deprecate old DS `Tag` component
  [(#1103)](https://github.com/empathyco/x/pull/1103)

## [3.0.0-alpha.334](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.333...@empathyco/x-components@3.0.0-alpha.334) (2023-03-16)

### Features

- **plugin:** replace old bus implementation using the new `x-priority-bus`
  [(#1086)](https://github.com/empathyco/x/pull/1086)

## [3.0.0-alpha.333](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.332...@empathyco/x-components@3.0.0-alpha.333) (2023-03-15)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.332](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.331...@empathyco/x-components@3.0.0-alpha.332) (2023-03-14)

### Features

- **design-system:** add XDS badge component [(#1100)](https://github.com/empathyco/x/pull/1100)

## [3.0.0-alpha.331](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.330...@empathyco/x-components@3.0.0-alpha.331) (2023-03-14)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.330](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.329...@empathyco/x-components@3.0.0-alpha.330) (2023-03-09)

### Code Refactoring

- **components:** migrate `AutoProgressBar` to `Composition API`
  [(#1087)](https://github.com/empathyco/x/pull/1087)

## [3.0.0-alpha.329](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.328...@empathyco/x-components@3.0.0-alpha.329) (2023-03-09)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.328](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.327...@empathyco/x-components@3.0.0-alpha.328) (2023-03-07)

### Bug Fixes

- **edocs-live-examples:** Live example was not rendered

## [3.0.0-alpha.327](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.326...@empathyco/x-components@3.0.0-alpha.327) (2023-03-07)

### Bug Fixes

- **deps:** remove `only-allow` pnpm [(#1097)](https://github.com/empathyco/x/pull/1097)

### Documentation

- **related-tags:** added curation options [(#1095)](https://github.com/empathyco/x/pull/1095)

## [3.0.0-alpha.326](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.325...@empathyco/x-components@3.0.0-alpha.326) (2023-03-06)

### Documentation

- **integration:** add close api function [(#1096)](https://github.com/empathyco/x/pull/1096)

## [3.0.0-alpha.325](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.324...@empathyco/x-components@3.0.0-alpha.325) (2023-03-02)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.324](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.323...@empathyco/x-components@3.0.0-alpha.324) (2023-03-02)

### Features

- **queries-preview:** add query preview list component to orchestrate requests
  [(#1084)](https://github.com/empathyco/x/pull/1084)

## [3.0.0-alpha.323](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.322...@empathyco/x-components@3.0.0-alpha.323) (2023-03-01)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.322](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.321...@empathyco/x-components@3.0.0-alpha.322) (2023-03-01)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.321](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.320...@empathyco/x-components@3.0.0-alpha.321) (2023-03-01)

### Features

- Add close event to BaseXAPI [(#1091)](https://github.com/empathyco/x/pull/1091)

### Bug Fixes

- **design-system:** fix deprecated typography and picture components
  [(#1090)](https://github.com/empathyco/x/pull/1090)

## [3.0.0-alpha.320](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.319...@empathyco/x-components@3.0.0-alpha.320) (2023-02-28)

### Bug Fixes

- **components:** Fix open issue when focused on body. Fix `SearchInputPlaceholder` styles.
  [(#1078)](https://github.com/empathyco/x/pull/1078)

## [3.0.0-alpha.319](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.318...@empathyco/x-components@3.0.0-alpha.319) (2023-02-27)

### Features

- **banner:** add support without title and no clickable
  [(#1069)](https://github.com/empathyco/x/pull/1069)

## [3.0.0-alpha.318](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.317...@empathyco/x-components@3.0.0-alpha.318) (2023-02-21)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.317](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.316...@empathyco/x-components@3.0.0-alpha.317) (2023-02-17)

### Build System

- **dependencies:** bump `@bahmutov/cypress-esbuild-preprocessor` from `2.1.5` to `2.2.0`
  [(#1082)](https://github.com/empathyco/x/pull/1082)

## [3.0.0-alpha.316](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.315...@empathyco/x-components@3.0.0-alpha.316) (2023-02-16)

### Features

- remove `x-suggestion` class from `BaseSuggestion` component
  [(#1077)](https://github.com/empathyco/x/pull/1077)

## [3.0.0-alpha.315](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.314...@empathyco/x-components@3.0.0-alpha.315) (2023-02-15)

### Features

- **design-system:** Add `Input Group` component to the X Design System.
  [(#1066)](https://github.com/empathyco/x/pull/1066)

## [3.0.0-alpha.314](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.313...@empathyco/x-components@3.0.0-alpha.314) (2023-02-15)

### Features

- **design-system:** Add layout `layout-stack` util.
  [(#1076)](https://github.com/empathyco/x/pull/1076)

## [3.0.0-alpha.313](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.312...@empathyco/x-components@3.0.0-alpha.313) (2023-02-14)

### ⚠ BREAKING CHANGES

- **design-system:** design system scroll styles are deprecated. To continue using them import from
  deprecated-full-theme.css

### Features

- **design-system:** deprecate old x-scroll styles
  [(#1073)](https://github.com/empathyco/x/pull/1073)

### Bug Fixes

- **modal:** set focusOnOpen for the main-modal to false
  [(#1074)](https://github.com/empathyco/x/pull/1074)

## [3.0.0-alpha.312](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.311...@empathyco/x-components@3.0.0-alpha.312) (2023-02-14)

### Build System

- Delete unused `Jenkinsfile`. [(#1075)](https://github.com/empathyco/x/pull/1075)

## [3.0.0-alpha.311](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.310...@empathyco/x-components@3.0.0-alpha.311) (2023-02-10)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.310](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.309...@empathyco/x-components@3.0.0-alpha.310) (2023-02-08)

### Bug Fixes

- **search:** reset `query`, `page` and `sort` on clear query
  [(#1045)](https://github.com/empathyco/x/pull/1045)

### Continuous Integration

- refactor `lint` command to benefit from `nx parallelisation`
  [(#1051)](https://github.com/empathyco/x/pull/1051)

## [3.0.0-alpha.309](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.308...@empathyco/x-components@3.0.0-alpha.309) (2023-02-07)

### Continuous Integration

- migrate from `npm` & `lerna bootstrap` to `pnpm`
  [(#1047)](https://github.com/empathyco/x/pull/1047)

## [3.0.0-alpha.308](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.307...@empathyco/x-components@3.0.0-alpha.308) (2023-02-06)

### ⚠ BREAKING CHANGES

- **design-system:** Old design-system `Icon` styles are now located in the
  `deprecated-full-theme.css` file. Removed `checkbox-card`, `nq1`, `nq2`, `nq3`, and `nq4 icons`.

### Features

- **design-system:** add `icon` to XDS [(#1053)](https://github.com/empathyco/x/pull/1053)

## [3.0.0-alpha.307](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.306...@empathyco/x-components@3.0.0-alpha.307) (2023-02-03)

### Build System

- **deps:** update deps [(#1062)](https://github.com/empathyco/x/pull/1062)

## [3.0.0-alpha.306](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.305...@empathyco/x-components@3.0.0-alpha.306) (2023-02-01)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.305](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.304...@empathyco/x-components@3.0.0-alpha.305) (2023-01-30)

### Features

- **history-queries:** emit click event on HistoryQuery click
  [(#1048)](https://github.com/empathyco/x/pull/1048)

## [3.0.0-alpha.304](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.303...@empathyco/x-components@3.0.0-alpha.304) (2023-01-30)

### Features

- **history-queries:** bind formatTime callback to MyHistory suggestion slot
  [(#1049)](https://github.com/empathyco/x/pull/1049)

## [3.0.0-alpha.303](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.302...@empathyco/x-components@3.0.0-alpha.303) (2023-01-27)

### Build System

- **deps:** update deps [(#1046)](https://github.com/empathyco/x/pull/1046)

## [3.0.0-alpha.302](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.301...@empathyco/x-components@3.0.0-alpha.302) (2023-01-26)

### ⚠ BREAKING CHANGES

- **components:** class `x-picture__image` renamed to `x-picture-image`, deprecate classes
  `x-picture__image--placeholder` and `x-picture__image--fallback`

### Features

- **components:** deprecate x-picture\_\_image and placeholder/fallback styles
  [(#1036)](https://github.com/empathyco/x/pull/1036)

## [3.0.0-alpha.301](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.300...@empathyco/x-components@3.0.0-alpha.301) (2023-01-25)

### Documentation

- correcting `video-reference` id [(#1038)](https://github.com/empathyco/x/pull/1038)

## [3.0.0-alpha.300](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.299...@empathyco/x-components@3.0.0-alpha.300) (2023-01-25)

### Build System

- **dependencies:** update `typescript` to `4.9.4` and its dependencies to their latest version
  [(#993)](https://github.com/empathyco/x/pull/993)

## [3.0.0-alpha.299](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.298...@empathyco/x-components@3.0.0-alpha.299) (2023-01-24)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.298](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.297...@empathyco/x-components@3.0.0-alpha.298) (2023-01-24)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.297](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.296...@empathyco/x-components@3.0.0-alpha.297) (2023-01-24)

### Features

- add `prettier-plugin-tailwindcss` [(#1033)](https://github.com/empathyco/x/pull/1033)

## [3.0.0-alpha.296](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.295...@empathyco/x-components@3.0.0-alpha.296) (2023-01-24)

### Features

- remove duplicates from image placeholder/fallback classes
  [(#1032)](https://github.com/empathyco/x/pull/1032)

## [3.0.0-alpha.295](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.294...@empathyco/x-components@3.0.0-alpha.295) (2023-01-24)

### ⚠ BREAKING CHANGES

- **components:** Renamed `SlidingPanel` css classes `x-sliding-panel--at-start` and
  `x-sliding-panel--at-end` to `x-sliding-panel-at-start` and `x-sliding-panel-at-end` respectively.
- **components:** Renamed `SlidingPanel` buttons css classes `x-sliding-panel__button-left` and
  `x-sliding-panel__button-right` to `x-sliding-panel-button-left` and
  `x-sliding-panel-button-right` respectively.
- **components:** Old design-system `SlidingPanel` styles (including the updated button classes) are
  now located in the `deprecated-full-theme.css` file.

### Features

- **components:** use XDS `sliding panel` [(#1028)](https://github.com/empathyco/x/pull/1028)

## [3.0.0-alpha.294](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.293...@empathyco/x-components@3.0.0-alpha.294) (2023-01-23)

### ⚠ BREAKING CHANGES

- **design-system:** `picture` and some `result` styles related are now deprecated. To continue
  using them import from `deprecated-full-theme.css`.
- Rename `x-result-picture__image` to `x-result-picture-image`.

### Features

- **design-system:** add `product-image` `XDS` component
  [(#1025)](https://github.com/empathyco/x/pull/1025)

## [3.0.0-alpha.293](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.292...@empathyco/x-components@3.0.0-alpha.293) (2023-01-23)

### Styling

- update prettier and format code [(#1026)](https://github.com/empathyco/x/pull/1026)

## [3.0.0-alpha.292](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.291...@empathyco/x-components@3.0.0-alpha.292) (2023-01-23)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.291](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.290...@empathyco/x-components@3.0.0-alpha.291) (2023-01-20)

### Build System

- **deps:** update dependencies [(#1024)](https://github.com/empathyco/x/pull/1024)

## [3.0.0-alpha.290](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.289...@empathyco/x-components@3.0.0-alpha.290) (2023-01-20)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.289](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.288...@empathyco/x-components@3.0.0-alpha.289) (2023-01-19)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.288](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.287...@empathyco/x-components@3.0.0-alpha.288) (2023-01-18)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.287](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.286...@empathyco/x-components@3.0.0-alpha.287) (2023-01-18)

### Features

- **components:** add `contentClass` to `modals` [(#1009)](https://github.com/empathyco/x/pull/1009)

## [3.0.0-alpha.286](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.285...@empathyco/x-components@3.0.0-alpha.286) (2023-01-18)

### ⚠ BREAKING CHANGES

- **history-queries:** Renamed `removeHistoryQueryClass` prop to `removeButtonClass`.

### Features

- **history-queries:** add dynamic classes to the history query suggestion
  [(#1014)](https://github.com/empathyco/x/pull/1014)

## [3.0.0-alpha.285](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.284...@empathyco/x-components@3.0.0-alpha.285) (2023-01-17)

### ⚠ BREAKING CHANGES

- Rename `x-grid` class to `x-grid-list`.
- Rename `x-grid__item` class to `x-grid-list__item`.
- Rename `x-grid--cols-{cols}` class to `x-grid-list--cols-{cols}`.

### Features

- rename `x-grid` class to `x-grid-list` [(#1015)](https://github.com/empathyco/x/pull/1015)

## [3.0.0-alpha.284](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.283...@empathyco/x-components@3.0.0-alpha.284) (2023-01-17)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.283](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.282...@empathyco/x-components@3.0.0-alpha.283) (2023-01-17)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.282](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.281...@empathyco/x-components@3.0.0-alpha.282) (2023-01-17)

### Features

- add dynamic classes to the suggestion item inside the `base-suggestions`
  [(#1008)](https://github.com/empathyco/x/pull/1008)

## [3.0.0-alpha.281](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.280...@empathyco/x-components@3.0.0-alpha.281) (2023-01-16)

### Features

- **history-queries:** add dynamic classes to the remove history query button
  [(#1007)](https://github.com/empathyco/x/pull/1007)

## [3.0.0-alpha.280](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.279...@empathyco/x-components@3.0.0-alpha.280) (2023-01-13)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.279](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.278...@empathyco/x-components@3.0.0-alpha.279) (2023-01-13)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.278](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.277...@empathyco/x-components@3.0.0-alpha.278) (2023-01-13)

### Build System

- **deps:** update dependencies [(#1004)](https://github.com/empathyco/x/pull/1004)

## [3.0.0-alpha.277](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.276...@empathyco/x-components@3.0.0-alpha.277) (2023-01-12)

### Documentation

- assets migration [(#995)](https://github.com/empathyco/x/pull/995)

## [3.0.0-alpha.276](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.275...@empathyco/x-components@3.0.0-alpha.276) (2023-01-11)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.275](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.274...@empathyco/x-components@3.0.0-alpha.275) (2023-01-10)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.274](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.273...@empathyco/x-components@3.0.0-alpha.274) (2023-01-09)

### Features

- **history-queries:** expose `historyQueriesWithResults` in the alias API
  [(#991)](https://github.com/empathyco/x/pull/991)

## [3.0.0-alpha.273](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.272...@empathyco/x-components@3.0.0-alpha.273) (2023-01-09)

### ⚠ BREAKING CHANGES

- **design-system:** suggestion and suggestion group styles are now deprecated. To continue using
  them import from `deprecated-full-theme.css`.

### Features

- **design-system:** deprecate old suggestion and suggestion group styles
  [(#975)](https://github.com/empathyco/x/pull/975)

## [3.0.0-alpha.272](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.271...@empathyco/x-components@3.0.0-alpha.272) (2023-01-09)

### Features

- **design-system:** deprecate old typography styles
  [(#973)](https://github.com/empathyco/x/pull/973)

## [3.0.0-alpha.271](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.270...@empathyco/x-components@3.0.0-alpha.271) (2023-01-06)

### Build System

- **deps:** update dependencies

## [3.0.0-alpha.270](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.269...@empathyco/x-components@3.0.0-alpha.270) (2023-01-04)

### Features

- rename `search-types` to `x-types` [(#928)](https://github.com/empathyco/x/pull/928)

## [3.0.0-alpha.269](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.268...@empathyco/x-components@3.0.0-alpha.269) (2023-01-04)

### Features

- add view to test base-result-link accessibility [(#972)](https://github.com/empathyco/x/pull/972)

## [3.0.0-alpha.268](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.267...@empathyco/x-components@3.0.0-alpha.268) (2023-01-03)

### Build System

- **deps:** update `vue` to version `2.7` [(#971)](https://github.com/empathyco/x/pull/971)

## [3.0.0-alpha.267](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.266...@empathyco/x-components@3.0.0-alpha.267) (2023-01-03)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.266](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.265...@empathyco/x-components@3.0.0-alpha.266) (2023-01-02)

### Continuous Integration

- make Cypress cache depend on package. Make eslint cache restore last version if no exact match.

## [3.0.0-alpha.265](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.264...@empathyco/x-components@3.0.0-alpha.265) (2022-12-30)

### Testing

- **e2e:** update `cypress` to version `12.1.0` and replace `cypress-cucumber-preprocessor` with
  `@badeball/cypress-cucumber-preprocessor` [(#747)](https://github.com/empathyco/x/pull/747)

## [3.0.0-alpha.264](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.263...@empathyco/x-components@3.0.0-alpha.264) (2022-12-30)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.263](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.262...@empathyco/x-components@3.0.0-alpha.263) (2022-12-30)

### Features

- **design-system:** Add suggestion group component
  [(#943)](https://github.com/empathyco/x/pull/943)

## [3.0.0-alpha.262](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.261...@empathyco/x-components@3.0.0-alpha.262) (2022-12-29)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.261](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.260...@empathyco/x-components@3.0.0-alpha.261) (2022-12-29)

### Bug Fixes

- **build:** use the default `vue-cli` `webpack` configuration in `rollup-plugin-vue`
  [(#961)](https://github.com/empathyco/x/pull/961)

## [3.0.0-alpha.260](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.259...@empathyco/x-components@3.0.0-alpha.260) (2022-12-26)

### Documentation

- fix typo in UrlHandler docs [(#959)](https://github.com/empathyco/x/pull/959)

## [3.0.0-alpha.259](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.258...@empathyco/x-components@3.0.0-alpha.259) (2022-12-26)

### Features

- modify base-events-modal-close and base-events-modal-open for WCAG compliance
  [(#946)](https://github.com/empathyco/x/pull/946)

## [3.0.0-alpha.258](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.257...@empathyco/x-components@3.0.0-alpha.258) (2022-12-26)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.257](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.256...@empathyco/x-components@3.0.0-alpha.257) (2022-12-23)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.256](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.255...@empathyco/x-components@3.0.0-alpha.256) (2022-12-22)

### Bug Fixes

- **components:** image flickering on re-rendering [(#945)](https://github.com/empathyco/x/pull/945)

## [3.0.0-alpha.255](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.254...@empathyco/x-components@3.0.0-alpha.255) (2022-12-22)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.254](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.253...@empathyco/x-components@3.0.0-alpha.254) (2022-12-20)

### ⚠ BREAKING CHANGES

- Rename `NextQueryPreviewMounted` to `NextQueryPreviewMountedHook` and `QueryPreviewRemoved` to
  `QueryPreviewUnmountedHook`

### Features

- Rename lifecycle hook events [(#939)](https://github.com/empathyco/x/pull/939)
- **scroll:** capture listeners in MainScrollItem component
  [(#942)](https://github.com/empathyco/x/pull/942)

## [3.0.0-alpha.253](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.252...@empathyco/x-components@3.0.0-alpha.253) (2022-12-19)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.252](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.251...@empathyco/x-components@3.0.0-alpha.252) (2022-12-16)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.251](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.250...@empathyco/x-components@3.0.0-alpha.251) (2022-12-15)

### Documentation

- use new docs video reference component [(#923)](https://github.com/empathyco/x/pull/923)

## [3.0.0-alpha.250](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.249...@empathyco/x-components@3.0.0-alpha.250) (2022-12-15)

### Continuous Integration

- use matrix steps and jest projects [(#919)](https://github.com/empathyco/x/pull/919)

## [3.0.0-alpha.249](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.248...@empathyco/x-components@3.0.0-alpha.249) (2022-12-14)

### Features

- **recommendations:** emit `RecommendationsChanged`
  [(#922)](https://github.com/empathyco/x/pull/922)

## [3.0.0-alpha.248](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.247...@empathyco/x-components@3.0.0-alpha.248) (2022-12-12)

### Bug Fixes

- remove warning when the event is not defined [(#918)](https://github.com/empathyco/x/pull/918)

## [3.0.0-alpha.247](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.246...@empathyco/x-components@3.0.0-alpha.247) (2022-12-09)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.246](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.245...@empathyco/x-components@3.0.0-alpha.246) (2022-12-09)

### Build System

- **deps:** update dependencies [(#908)](https://github.com/empathyco/x/pull/908)

### Code Refactoring

- **plugin:** Rename `inputStatus` to `searchBoxStatus` in Alias API.
  [(#913)](https://github.com/empathyco/x/pull/913)

## [3.0.0-alpha.245](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.244...@empathyco/x-components@3.0.0-alpha.245) (2022-12-09)

### Features

- **search-box:** add input status handling[(#903)](https://github.com/empathyco/x/pull/903)

## [3.0.0-alpha.244](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.243...@empathyco/x-components@3.0.0-alpha.244) (2022-12-08)

### ⚠ BREAKING CHANGES

- Removes `queryHTML` slot scope prop from `BaseSuggestion`, `PopularSearch` `QuerySuggestion` and
  `HistoryQuery`. Use the new `Highlight` component instead.

### Features

- **components:** Use `Highlight` component inside suggestion
  components.[(#894)](https://github.com/empathyco/x/pull/894)

## [3.0.0-alpha.243](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.242...@empathyco/x-components@3.0.0-alpha.243) (2022-12-08)

### Testing

- **e2e:** make `HistoryQueries` test wait for no results
  [(#906)](https://github.com/empathyco/x/pull/906)

## [3.0.0-alpha.242](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.241...@empathyco/x-components@3.0.0-alpha.242) (2022-12-07)

### ⚠ BREAKING CHANGES

- the event `SearchResponseProvided` was renamed to `SearchResponseChanged`

### Code Refactoring

- Simplify suggestions list slots. [(#893)](https://github.com/empathyco/x/pull/893)

## [3.0.0-alpha.241](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.240...@empathyco/x-components@3.0.0-alpha.241) (2022-12-06)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.240](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.239...@empathyco/x-components@3.0.0-alpha.240) (2022-12-02)

### Features

- **history-queries:** Hide history queries with no results
  [(#865)](https://github.com/empathyco/x/pull/865)

## [3.0.0-alpha.239](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.238...@empathyco/x-components@3.0.0-alpha.239) (2022-12-01)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.238](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.237...@empathyco/x-components@3.0.0-alpha.238) (2022-12-01)

### Features

- **components:** add `getTargetElement` util to retrieve the `event.target`
  [(#870)](https://github.com/empathyco/x/pull/870)

### Bug Fixes

- **components:** reset`BaseResultImage` images state when `result` `prop` changes
  [(#888)](https://github.com/empathyco/x/pull/888)

## [3.0.0-alpha.237](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.236...@empathyco/x-components@3.0.0-alpha.237) (2022-12-01)

### Features

- **recommendations:** add `updateRecommendation` mutation
  [(#891)](https://github.com/empathyco/x/pull/891)

## [3.0.0-alpha.236](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.235...@empathyco/x-components@3.0.0-alpha.236) (2022-11-29)

### Features

- **tabs-panel:** add base tabs panel component [(#871)](https://github.com/empathyco/x/pull/871)

## [3.0.0-alpha.235](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.234...@empathyco/x-components@3.0.0-alpha.235) (2022-11-29)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.234](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.233...@empathyco/x-components@3.0.0-alpha.234) (2022-11-29)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.233](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.232...@empathyco/x-components@3.0.0-alpha.233) (2022-11-28)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.232](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.231...@empathyco/x-components@3.0.0-alpha.232) (2022-11-28)

### Features

- add `Highlight` component [(#872)](https://github.com/empathyco/x/pull/872)

## [3.0.0-alpha.231](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.230...@empathyco/x-components@3.0.0-alpha.231) (2022-11-28)

### ⚠ BREAKING CHANGES

- **components:** Renamed prop `animation` of `BaseResultImage` to `loadAnimation`.

### Features

- show next result image on hover [(#863)](https://github.com/empathyco/x/pull/863)

### Bug Fixes

- **components:** Fix InfiniteScroll get root element inside Shadow DOM.
  [(#874)](https://github.com/empathyco/x/pull/874)

## [3.0.0-alpha.230](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.229...@empathyco/x-components@3.0.0-alpha.230) (2022-11-24)

### Features

- Emit SearchResponseProvided event from Search Module
  [(#864)](https://github.com/empathyco/x/pull/864)

## [3.0.0-alpha.229](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.228...@empathyco/x-components@3.0.0-alpha.229) (2022-11-22)

### Features

- **components:** make base dropdown based components accessible
  [(#846)](https://github.com/empathyco/x/pull/846)

### Bug Fixes

- make `appear` attribute configurable on animations that have it set to `true` by default
  [(#862)](https://github.com/empathyco/x/pull/862)

## [3.0.0-alpha.228](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.227...@empathyco/x-components@3.0.0-alpha.228) (2022-11-17)

### Features

- adding e-docs portal live preview

## [3.0.0-alpha.227](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.226...@empathyco/x-components@3.0.0-alpha.227) (2022-11-15)

### Features

- **design-system:** add `suggestion` component to the XDS
  [(#838)](https://github.com/empathyco/x/pull/838)
- history-queries-switch wai aria adjustments [(#847)](https://github.com/empathyco/x/pull/847)

## [3.0.0-alpha.226](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.225...@empathyco/x-components@3.0.0-alpha.226) (2022-11-14)

### Features

- Change suggestion components to bind $attrs to base suggestions
  [(#831)](https://github.com/empathyco/x/pull/831)

## [3.0.0-alpha.225](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.224...@empathyco/x-components@3.0.0-alpha.225) (2022-11-11)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.224](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.223...@empathyco/x-components@3.0.0-alpha.224) (2022-11-11)

### Bug Fixes

- **animations:** make content-visibility CSS property and createCollapseAnimationMixin work
  together [(#839)](https://github.com/empathyco/x/pull/839)

## [3.0.0-alpha.223](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.222...@empathyco/x-components@3.0.0-alpha.223) (2022-11-10)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.222](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.221...@empathyco/x-components@3.0.0-alpha.222) (2022-11-10)

### Features

- **x-plugin:** Add function as possible value of `domElement` in
  InstallXOptions.[(#836)](https://github.com/empathyco/x/pull/836)

## [3.0.0-alpha.221](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.220...@empathyco/x-components@3.0.0-alpha.221) (2022-11-10)

### Features

- place modal under selected element [(#829)](https://github.com/empathyco/x/pull/829)

## [3.0.0-alpha.220](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.219...@empathyco/x-components@3.0.0-alpha.220) (2022-11-09)

### Features

- **empathize:** show Empathize only when it has content
  [(#820)](https://github.com/empathyco/x/pull/820)

## [3.0.0-alpha.219](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.218...@empathyco/x-components@3.0.0-alpha.219) (2022-11-09)

### Features

- **tagging:** track banner clicks [(#822)](https://github.com/empathyco/x/pull/822)

## [3.0.0-alpha.218](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.217...@empathyco/x-components@3.0.0-alpha.218) (2022-11-09)

### ⚠ BREAKING CHANGES

- **design-system:** the old design system button styles are now located in the
  `deprecated-full-theme.css`, if setup is not using the new design system, it must import this
  file.

### Features

- **design-system:** deprecate old design system button styles
  [(#830)](https://github.com/empathyco/x/pull/830)

## [3.0.0-alpha.217](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.216...@empathyco/x-components@3.0.0-alpha.217) (2022-11-08)

### Bug Fixes

- remove `resize-observer-browser` types from tsconfig
  [(#833)](https://github.com/empathyco/x/pull/833)

## [3.0.0-alpha.216](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.215...@empathyco/x-components@3.0.0-alpha.216) (2022-11-08)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.215](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.214...@empathyco/x-components@3.0.0-alpha.215) (2022-11-04)

### Features

- wai-aria for BaseEventButton based components [(#816)](https://github.com/empathyco/x/pull/816)

## [3.0.0-alpha.214](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.213...@empathyco/x-components@3.0.0-alpha.214) (2022-11-03)

### Features

- **design-system:** add tailwind showcase component
  [(#778)](https://github.com/empathyco/x/pull/778)

## [3.0.0-alpha.213](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.212...@empathyco/x-components@3.0.0-alpha.213) (2022-11-03)

### Features

- Use Banner position (= row) to sort grid [(#802)](https://github.com/empathyco/x/pull/802)

## [3.0.0-alpha.212](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.211...@empathyco/x-components@3.0.0-alpha.212) (2022-11-03)

### ⚠ BREAKING CHANGES

- **components:** `facets` are now optional in `Suggestion`.

### Features

- **components:** add filters to base-suggestions [(#758)](https://github.com/empathyco/x/pull/758)

## [3.0.0-alpha.211](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.210...@empathyco/x-components@3.0.0-alpha.211) (2022-11-02)

### Features

- **components:** insert promoteds in the grid using position
  [(#801)](https://github.com/empathyco/x/pull/801)

### Bug Fixes

- make promoted and banner position optional [(#817)](https://github.com/empathyco/x/pull/817)

## [3.0.0-alpha.210](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.209...@empathyco/x-components@3.0.0-alpha.210) (2022-11-02)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.209](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.208...@empathyco/x-components@3.0.0-alpha.209) (2022-11-02)

### Features

- **components:** Emit ColumnsNumberRendered event on BaseGrid
  [(#806)](https://github.com/empathyco/x/pull/806)

## [3.0.0-alpha.208](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.207...@empathyco/x-components@3.0.0-alpha.208) (2022-11-02)

### Features

- apply dynamic css mixin to sliding panel and column picker list buttons
  [(#815)](https://github.com/empathyco/x/pull/815)

## [3.0.0-alpha.207](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.206...@empathyco/x-components@3.0.0-alpha.207) (2022-11-02)

### Bug Fixes

- type empathize events and replace UserPressedEnter with UserPressedEnterKey

## [3.0.0-alpha.206](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.205...@empathyco/x-components@3.0.0-alpha.206) (2022-10-31)

### Features

- add `dynamic-props` mixin [(#798)](https://github.com/empathyco/x/pull/798)

## [3.0.0-alpha.205](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.204...@empathyco/x-components@3.0.0-alpha.205) (2022-10-31)

### Features

- add position on Banner and Promoted models [(#800)](https://github.com/empathyco/x/pull/800)

## [3.0.0-alpha.204](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.203...@empathyco/x-components@3.0.0-alpha.204) (2022-10-27)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.203](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.202...@empathyco/x-components@3.0.0-alpha.203) (2022-10-26)

### Features

- **design-system:** add zoom effect [(#799)](https://github.com/empathyco/x/pull/799)

## [3.0.0-alpha.202](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.201...@empathyco/x-components@3.0.0-alpha.202) (2022-10-24)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.201](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.200...@empathyco/x-components@3.0.0-alpha.201) (2022-10-21)

### ⚠ BREAKING CHANGES

- **tagging:** `tagging` property of `Taggable` and `queryTagging` property of `SearchResponse` are
  optional.

### Features

- **tagging:** make `tagging` and `queryTagging` optional
  [(#797)](https://github.com/empathyco/x/pull/797)

## [3.0.0-alpha.200](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.199...@empathyco/x-components@3.0.0-alpha.200) (2022-10-21)

### Continuous Integration

- export webpack config from `x-archetype-utils` [(#760)](https://github.com/empathyco/x/pull/760)

## [3.0.0-alpha.199](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.198...@empathyco/x-components@3.0.0-alpha.199) (2022-10-20)

### Documentation

- **functional:** titles refactor and change image source
  [(#790)](https://github.com/empathyco/x/pull/790)

## [3.0.0-alpha.198](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.197...@empathyco/x-components@3.0.0-alpha.198) (2022-10-20)

### Bug Fixes

- **related-tags:** use `query` instead of `tag` as `key` to ensure unique values
  [(#792)](https://github.com/empathyco/x/pull/792)

## [3.0.0-alpha.197](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.196...@empathyco/x-components@3.0.0-alpha.197) (2022-10-19)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.196](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.195...@empathyco/x-components@3.0.0-alpha.196) (2022-10-19)

### Features

- **search-box:** add `SearchInputPlaceholder` component
  [(#771)](https://github.com/empathyco/x/pull/771)

## [3.0.0-alpha.195](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.194...@empathyco/x-components@3.0.0-alpha.195) (2022-10-19)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.194](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.193...@empathyco/x-components@3.0.0-alpha.194) (2022-10-18)

### Features

- **components:** Add new origins to the `animateClipPath` animation factory.
  [(#777)](https://github.com/empathyco/x/pull/777)

## [3.0.0-alpha.193](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.192...@empathyco/x-components@3.0.0-alpha.193) (2022-10-17)

### Testing

- **next-queries:** next queries preview e2e tests [(#759)](https://github.com/empathyco/x/pull/759)

## [3.0.0-alpha.192](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.191...@empathyco/x-components@3.0.0-alpha.192) (2022-10-14)

### Continuous Integration

- update `runners` version [(#740)](https://github.com/empathyco/x/pull/740)

## [3.0.0-alpha.191](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.190...@empathyco/x-components@3.0.0-alpha.191) (2022-10-13)

### Features

- Add directional origins for translate animations [(#773)](https://github.com/empathyco/x/pull/773)
- Add search input hover events [(#772)](https://github.com/empathyco/x/pull/772)

## [3.0.0-alpha.190](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.189...@empathyco/x-components@3.0.0-alpha.190) (2022-10-12)

### Features

- hidde overflow-y in the sliding panel [(#768)](https://github.com/empathyco/x/pull/768)

## [3.0.0-alpha.189](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.188...@empathyco/x-components@3.0.0-alpha.189) (2022-10-06)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.188](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.187...@empathyco/x-components@3.0.0-alpha.188) (2022-10-05)

### Bug Fixes

- wait for the extra params to make the initial requests
  [(#754)](https://github.com/empathyco/x/pull/754)

## [3.0.0-alpha.187](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.186...@empathyco/x-components@3.0.0-alpha.187) (2022-10-05)

### Features

- **queries-preview:** Add `debounceTimeMs` to `QueryPreview` component.
  [(#752)](https://github.com/empathyco/x/pull/752)

## [3.0.0-alpha.186](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.185...@empathyco/x-components@3.0.0-alpha.186) (2022-10-03)

### Features

- make `adapter` configurable in the `home` view [(#750)](https://github.com/empathyco/x/pull/750)

## [3.0.0-alpha.185](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.184...@empathyco/x-components@3.0.0-alpha.185) (2022-09-30)

### Bug Fixes

- **base-modal:** add prop to allow the modal to move the focus to an element within it on open

## [3.0.0-alpha.184](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.183...@empathyco/x-components@3.0.0-alpha.184) (2022-09-30)

### Continuous Integration

- silent jest and eslint warnings [(#749)](https://github.com/empathyco/x/pull/749)

## [3.0.0-alpha.183](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.182...@empathyco/x-components@3.0.0-alpha.183) (2022-09-29)

### Features

- **next-queries:** add `origin` to `next queries preview`
  [(#746)](https://github.com/empathyco/x/pull/746)

## [3.0.0-alpha.182](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.181...@empathyco/x-components@3.0.0-alpha.182) (2022-09-27)

### Bug Fixes

- **components:** restore scroll on `BaseModal` [(#736)](https://github.com/empathyco/x/pull/736)

### Documentation

- add `queriesPreview` to archetype integration [(#735)](https://github.com/empathyco/x/pull/735)

## [3.0.0-alpha.181](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.180...@empathyco/x-components@3.0.0-alpha.181) (2022-09-27)

### Features

- **queries-preview:** add `origin` to `QueryPreview` component
  [(#737)](https://github.com/empathyco/x/pull/737)

## [3.0.0-alpha.180](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.179...@empathyco/x-components@3.0.0-alpha.180) (2022-09-27)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.179](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.178...@empathyco/x-components@3.0.0-alpha.179) (2022-09-27)

### Features

- add `vue devtools` plugin to ease `XEvents` and `wiring` visualization
  [(#215)](https://github.com/empathyco/x/pull/215)

## [3.0.0-alpha.178](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.177...@empathyco/x-components@3.0.0-alpha.178) (2022-09-21)

### Features

- Improve `tailwindcss` types [(#730)](https://github.com/empathyco/x/pull/730)

## [3.0.0-alpha.177](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.176...@empathyco/x-components@3.0.0-alpha.177) (2022-09-21)

### Features

- **search-input:** prevent `<` or `>` input [(#433)](https://github.com/empathyco/x/pull/433)

## [3.0.0-alpha.176](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.175...@empathyco/x-components@3.0.0-alpha.176) (2022-09-20)

### Features

- Improve tailwindcss types. [(#725)](https://github.com/empathyco/x/pull/725)

## [3.0.0-alpha.175](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.174...@empathyco/x-components@3.0.0-alpha.175) (2022-09-20)

### Features

- **facets:** remove filters on new query [(#717)](https://github.com/empathyco/x/pull/717)

## [3.0.0-alpha.174](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.173...@empathyco/x-components@3.0.0-alpha.174) (2022-09-19)

### Features

- **design-system:** generate old design system tokens with tailwind values
  [(#675)](https://github.com/empathyco/x/pull/675)

## [3.0.0-alpha.173](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.172...@empathyco/x-components@3.0.0-alpha.173) (2022-09-16)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.172](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.171...@empathyco/x-components@3.0.0-alpha.172) (2022-09-13)

### Features

- **next-queries:** add `concatWhenNoMoreItems` prop
  [(#705)](https://github.com/empathyco/x/pull/705)

## [3.0.0-alpha.171](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.170...@empathyco/x-components@3.0.0-alpha.171) (2022-09-13)

### Features

- add `uiLang` parameter [(#714)](https://github.com/empathyco/x/pull/714)

## [3.0.0-alpha.170](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.169...@empathyco/x-components@3.0.0-alpha.170) (2022-09-09)

### Features

- **components:** add disable animation mixin [(#703)](https://github.com/empathyco/x/pull/703)
- disable `@typescript-eslint/no-extra-parens` rule
  [(#715)](https://github.com/empathyco/x/pull/715)

## [3.0.0-alpha.169](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.168...@empathyco/x-components@3.0.0-alpha.169) (2022-09-08)

### Features

- **search:** add `updateResult` mutation [(#706)](https://github.com/empathyco/x/pull/706)

## [3.0.0-alpha.168](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.167...@empathyco/x-components@3.0.0-alpha.168) (2022-09-07)

### Bug Fixes

- **components:** Fix the error on console in `BaseResultImage` with `CrossFade` Animation.
  [(#688)](https://github.com/empathyco/x/pull/688)

## [3.0.0-alpha.167](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.166...@empathyco/x-components@3.0.0-alpha.167) (2022-09-06)

### Features

- **queries-preview:** add query preview component [(#699)](https://github.com/empathyco/x/pull/699)

## [3.0.0-alpha.166](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.165...@empathyco/x-components@3.0.0-alpha.166) (2022-09-02)

### Bug Fixes

- Make `Home` grid next queries use grid data rather than state data.
  [(#687)](https://github.com/empathyco/x/pull/687)

## [3.0.0-alpha.165](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.164...@empathyco/x-components@3.0.0-alpha.165) (2022-08-31)

### Build System

- **dependencies:** fix Vue & Vuex versions [(#686)](https://github.com/empathyco/x/pull/686)

## [3.0.0-alpha.164](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.163...@empathyco/x-components@3.0.0-alpha.164) (2022-08-30)

### Features

- **queries-preview:** add wiring and actions [(#677)](https://github.com/empathyco/x/pull/677)

## [3.0.0-alpha.163](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.162...@empathyco/x-components@3.0.0-alpha.163) (2022-08-29)

### Documentation

- **functional:** add my history ui and related docs
  [(#685)](https://github.com/empathyco/x/pull/685)

## [3.0.0-alpha.162](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.161...@empathyco/x-components@3.0.0-alpha.162) (2022-08-29)

### Build System

- Support SSR with createInjectorSSR for styles. [(#674)](https://github.com/empathyco/x/pull/674)

## [3.0.0-alpha.161](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.160...@empathyco/x-components@3.0.0-alpha.161) (2022-08-26)

### Features

- **components:** variants auto selection [(#679)](https://github.com/empathyco/x/pull/679)

## [3.0.0-alpha.160](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.159...@empathyco/x-components@3.0.0-alpha.160) (2022-08-25)

### Features

- **components:** merge variant with the result [(#667)](https://github.com/empathyco/x/pull/667)

## [3.0.0-alpha.159](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.158...@empathyco/x-components@3.0.0-alpha.159) (2022-08-24)

### Documentation

- update functional docs callout formatting [(#671)](https://github.com/empathyco/x/pull/671)

## [3.0.0-alpha.158](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.156...@empathyco/x-components@3.0.0-alpha.158) (2022-08-24)

### Features

- **adapter:** disable cancel http client [(#658)](https://github.com/empathyco/x/pull/658)
- **queries-preview:** create `queriesPreview` module
  [(#670)](https://github.com/empathyco/x/pull/670)

### Bug Fixes

- conflict version [(#673)](https://github.com/empathyco/x/pull/673)

## [3.0.0-alpha.157](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.156...@empathyco/x-components@3.0.0-alpha.157) (2022-08-24)

### Features

- **queries-preview:** create `queriesPreview` module
  [(#670)](https://github.com/empathyco/x/pull/670)

## [3.0.0-alpha.156](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.155...@empathyco/x-components@3.0.0-alpha.156) (2022-08-19)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.155](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.154...@empathyco/x-components@3.0.0-alpha.155) (2022-08-18)

### Features

- **design-system:** add `tailwindcss` to `x-components` and configure it to use `x-tailwindcss`
  [(#655)](https://github.com/empathyco/x/pull/655)

## [3.0.0-alpha.154](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.153...@empathyco/x-components@3.0.0-alpha.154) (2022-08-12)

### Features

- add `queriesPreview` option to snippet config [(#654)](https://github.com/empathyco/x/pull/654)

## [3.0.0-alpha.153](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.152...@empathyco/x-components@3.0.0-alpha.153) (2022-08-10)

### Features

- **next-queries:** add `maxItemsToRender` prop to `NextQueryPreview` component
  [(#646)](https://github.com/empathyco/x/pull/646)

## [3.0.0-alpha.152](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.151...@empathyco/x-components@3.0.0-alpha.152) (2022-08-10)

### ⚠ BREAKING CHANGES

- **result:** `Result` model properties are optional, except `id`, `modelName` and `tagging`.

### Features

- **result:** add `variants` support [(#644)](https://github.com/empathyco/x/pull/644)

## [3.0.0-alpha.151](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.150...@empathyco/x-components@3.0.0-alpha.151) (2022-08-09)

### Documentation

- clarify how to subscribe to any `XEvent` [(#645)](https://github.com/empathyco/x/pull/645)

## [3.0.0-alpha.150](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.149...@empathyco/x-components@3.0.0-alpha.150) (2022-08-08)

### Features

- **components:** make `BaseIdModalOpen` rendering configurable
  [(#637)](https://github.com/empathyco/x/pull/637)

## [3.0.0-alpha.149](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.148...@empathyco/x-components@3.0.0-alpha.149) (2022-08-08)

### Bug Fixes

- **facets:** fix `SingleSelectModifier` handling for selecting hierar…
  [(#643)](https://github.com/empathyco/x/pull/643)

## [3.0.0-alpha.148](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.147...@empathyco/x-components@3.0.0-alpha.148) (2022-08-04)

### Features

- **next-queries:** add next query preview component
  [(#631)](https://github.com/empathyco/x/pull/631)

## [3.0.0-alpha.147](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.146...@empathyco/x-components@3.0.0-alpha.147) (2022-08-03)

### ⚠ BREAKING CHANGES

- **facets:** Removed the `setFilter`mutation from `facets` X-Module. Use `mutateFilter` instead.
- **facets:** Modified the `HierarchicalFilter.children` Model type. Now it is an
  `Array<HierarchicalFilter>` instead of an array of ids.

### Features

- **facets:** Move filters flattening from `x-adapter-platform` to `x-components`.
  [(#626)](https://github.com/empathyco/x/pull/626)

## [3.0.0-alpha.146](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.145...@empathyco/x-components@3.0.0-alpha.146) (2022-08-03)

### Documentation

- bring functional docs from eDocs project [(#630)](https://github.com/empathyco/x/pull/630)

## [3.0.0-alpha.145](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.144...@empathyco/x-components@3.0.0-alpha.145) (2022-08-01)

### Documentation

- update archetype integration and x-adapter docs [(#628)](https://github.com/empathyco/x/pull/628)

## [3.0.0-alpha.144](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.143...@empathyco/x-components@3.0.0-alpha.144) (2022-08-01)

### ⚠ BREAKING CHANGES

- `--x-number-aspect-ratio-picture` is now inverted. Previously value of 2 meant that it was twice
  taller than wider. Now it means twice wider than taller.

- feat(design-system): Re-do aspect ratio logic with modern `aspect-ratio` property

## [3.0.0-alpha.143](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.142...@empathyco/x-components@3.0.0-alpha.143) (2022-08-01)

### Features

- **components:** make `BaseIdModalClose` rendering configurable
  [(#627)](https://github.com/empathyco/x/pull/627)

## [3.0.0-alpha.142](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.141...@empathyco/x-components@3.0.0-alpha.142) (2022-07-29)

### Features

- Remove vue filters [(#635)](https://github.com/empathyco/x/pull/635)

## [3.0.0-alpha.141](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.140...@empathyco/x-components@3.0.0-alpha.141) (2022-07-28)

### Features

- **next-queries:** add next query preview logic [(#611)](https://github.com/empathyco/x/pull/611)

## [3.0.0-alpha.140](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.139...@empathyco/x-components@3.0.0-alpha.140) (2022-07-26)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.139](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.138...@empathyco/x-components@3.0.0-alpha.139) (2022-07-22)

### Features

- **history-queries:** disable `MyHistory` without confirmation when the `history queries` list is
  empty [(#615)](https://github.com/empathyco/x/pull/615)

## [3.0.0-alpha.138](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.137...@empathyco/x-components@3.0.0-alpha.138) (2022-07-22)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.137](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.136...@empathyco/x-components@3.0.0-alpha.137) (2022-07-21)

### Features

- **components:** add `MainModal`, `OpenMainModal` and `CloseMainModal`
  [(#609)](https://github.com/empathyco/x/pull/609)

## [3.0.0-alpha.136](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.135...@empathyco/x-components@3.0.0-alpha.136) (2022-07-21)

### Bug Fixes

- `pointer-events` affecting scrolling in sliding panel in `SingleColumnLayout` aside
  [(#614)](https://github.com/empathyco/x/pull/614)

## [3.0.0-alpha.135](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.134...@empathyco/x-components@3.0.0-alpha.135) (2022-07-21)

### Testing

- **e2e:** search modal re-opens properly after being closed
  [(#613)](https://github.com/empathyco/x/pull/613)

## [3.0.0-alpha.134](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.133...@empathyco/x-components@3.0.0-alpha.134) (2022-07-20)

### Bug Fixes

- **components:** now properly checks if it has content
  [(#612)](https://github.com/empathyco/x/pull/612)

## [3.0.0-alpha.133](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.132...@empathyco/x-components@3.0.0-alpha.133) (2022-07-15)

### Bug Fixes

- **components:** Add option to extend transitions with listeners and attributes
  [(#600)](https://github.com/empathyco/x/pull/600)

## [3.0.0-alpha.132](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.131...@empathyco/x-components@3.0.0-alpha.132) (2022-07-14)

### Features

- **history-queries:** add `UserClickedDismissDisableHistoryQueries` event

## [3.0.0-alpha.131](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.130...@empathyco/x-components@3.0.0-alpha.131) (2022-07-13)

### Features

- **history-queries:** add `HistoryQueriesSwitch` component
  [(#593)](https://github.com/empathyco/x/pull/593)

## [3.0.0-alpha.130](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.129...@empathyco/x-components@3.0.0-alpha.130) (2022-07-12)

### Features

- Move `XAPI` from `window.X` to `window.InterfaceX`
  [(#599)](https://github.com/empathyco/x/pull/599)

## [3.0.0-alpha.129](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.128...@empathyco/x-components@3.0.0-alpha.129) (2022-07-11)

### Features

- **history-queries:** bind `formatTime` to `suggestion-content` slot
  [(#598)](https://github.com/empathyco/x/pull/598)

## [3.0.0-alpha.128](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.127...@empathyco/x-components@3.0.0-alpha.128) (2022-07-11)

### Documentation

- Add module type to integration script docs [(#592)](https://github.com/empathyco/x/pull/592)

## [3.0.0-alpha.127](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.126...@empathyco/x-components@3.0.0-alpha.127) (2022-07-11)

### Features

- **components:** add new slot `extra-aside` to `SingleColumnLayout` and
  `FixedHeaderAndAsidesLayout` [(#591)](https://github.com/empathyco/x/pull/591)

## [3.0.0-alpha.126](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.125...@empathyco/x-components@3.0.0-alpha.126) (2022-07-07)

### Features

- **x-plugin:** add full `history queries` list to `alias API`

## [3.0.0-alpha.125](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.124...@empathyco/x-components@3.0.0-alpha.125) (2022-07-07)

### Features

- add settings icon [(#589)](https://github.com/empathyco/x/pull/589)

## [3.0.0-alpha.124](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.123...@empathyco/x-components@3.0.0-alpha.124) (2022-07-06)

### Features

- add 'my_history' as feature location [(#587)](https://github.com/empathyco/x/pull/587)
- **components:** add `BaseSwitch` component [(#586)](https://github.com/empathyco/x/pull/586)

### Testing

- fix exclude-filters e2e test [(#588)](https://github.com/empathyco/x/pull/588)

## [3.0.0-alpha.123](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.122...@empathyco/x-components@3.0.0-alpha.123) (2022-07-04)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.122](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.121...@empathyco/x-components@3.0.0-alpha.122) (2022-06-30)

### Code Refactoring

- Move aside to its own component in Home view. [(#581)](https://github.com/empathyco/x/pull/581)

## [3.0.0-alpha.121](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.120...@empathyco/x-components@3.0.0-alpha.121) (2022-06-29)

### Features

- **components:** add grid-4-col and update light-bulb icons
  [(#579)](https://github.com/empathyco/x/pull/579)

## [3.0.0-alpha.120](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.119...@empathyco/x-components@3.0.0-alpha.120) (2022-06-27)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.119](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.118...@empathyco/x-components@3.0.0-alpha.119) (2022-06-24)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.118](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.117...@empathyco/x-components@3.0.0-alpha.118) (2022-06-23)

### Features

- **identifier-results:** add maxItemsToRender prop
  [(#576)](https://github.com/empathyco/x/pull/576)

## [3.0.0-alpha.117](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.116...@empathyco/x-components@3.0.0-alpha.117) (2022-06-23)

### Features

- **components:** add radio button icons [(#574)](https://github.com/empathyco/x/pull/574)

### Bug Fixes

- Remove `@empathyco/x-platform-adapter` dependency from library code.
  [(#575)](https://github.com/empathyco/x/pull/575)

## [3.0.0-alpha.116](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.115...@empathyco/x-components@3.0.0-alpha.116) (2022-06-22)

### Features

- **facets:** Add slot by Facet ModelName. [(#572)](https://github.com/empathyco/x/pull/572)

## [3.0.0-alpha.115](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.114...@empathyco/x-components@3.0.0-alpha.115) (2022-06-21)

### Features

- remove old adapter package and use the new one [(#568)](https://github.com/empathyco/x/pull/568)

## [3.0.0-alpha.114](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.113...@empathyco/x-components@3.0.0-alpha.114) (2022-06-21)

### Build System

- sync duplicated dependencies [(#567)](https://github.com/empathyco/x/pull/567)

## [3.0.0-alpha.113](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.112...@empathyco/x-components@3.0.0-alpha.113) (2022-06-20)

### Features

- **adapter:** use the `x-adapter-platform` [(#565)](https://github.com/empathyco/x/pull/565)

## [3.0.0-alpha.112](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.111...@empathyco/x-components@3.0.0-alpha.112) (2022-06-17)

### Documentation

- fix broken link in x-components readme [(#561)](https://github.com/empathyco/x/pull/561)

## [3.0.0-alpha.111](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.110...@empathyco/x-components@3.0.0-alpha.111) (2022-06-16)

### Features

- **x-plugin:** add results to `Alias API` [(#545)](https://github.com/empathyco/x/pull/545)

## [3.0.0-alpha.110](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.109...@empathyco/x-components@3.0.0-alpha.110) (2022-06-16)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.109](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.108...@empathyco/x-components@3.0.0-alpha.109) (2022-06-13)

### Documentation

- add local storage info and data purposes

## [3.0.0-alpha.108](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.107...@empathyco/x-components@3.0.0-alpha.108) (2022-06-09)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.107](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.106...@empathyco/x-components@3.0.0-alpha.107) (2022-06-09)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.106](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.105...@empathyco/x-components@3.0.0-alpha.106) (2022-06-09)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.105](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.104...@empathyco/x-components@3.0.0-alpha.105) (2022-06-08)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.104](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.103...@empathyco/x-components@3.0.0-alpha.104) (2022-06-07)

### Features

- fix rest of warnings for accessibility

## [3.0.0-alpha.103](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.102...@empathyco/x-components@3.0.0-alpha.103) (2022-05-25)

### Documentation

- fix links and minor typos

## [3.0.0-alpha.102](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.101...@empathyco/x-components@3.0.0-alpha.102) (2022-05-19)

### Features

- **facets:** add `PreselectedFilters` component

## [3.0.0-alpha.101](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.100...@empathyco/x-components@3.0.0-alpha.101) (2022-05-18)

### Bug Fixes

- **related-tags:** related tags are now kept when navigating back

## [3.0.0-alpha.100](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.99...@empathyco/x-components@3.0.0-alpha.100) (2022-05-17)

### Bug Fixes

- **build:** supports being built on Windows based machines

## [3.0.0-alpha.99](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.98...@empathyco/x-components@3.0.0-alpha.99) (2022-05-17)

### Bug Fixes

- **url:** `query` is required to store params in the `URL`

## [3.0.0-alpha.98](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.97...@empathyco/x-components@3.0.0-alpha.98) (2022-05-13)

### Features

- fix form label warnings

## [3.0.0-alpha.97](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.96...@empathyco/x-components@3.0.0-alpha.97) (2022-05-13)

### Features

- move `response` types to `@empathyco/x-types`

## [3.0.0-alpha.96](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.95...@empathyco/x-components@3.0.0-alpha.96) (2022-05-13)

### ⚠ BREAKING CHANGES

- **facets:** Renamed method `registerFilterModifier` in `FilterEntityFactory` to
  `registerModifierByFacetId`.
- **facets:** Changed `modifiers` parameter of `registerFilterModifier` in `FilterEntityFactory`
  from single array in favour of rest parameters.

### Features

- **facets:** add `registerModifierByFilterModelName`

## [3.0.0-alpha.95](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.94...@empathyco/x-components@3.0.0-alpha.95) (2022-05-11)

### ⚠ BREAKING CHANGES

- Request types moved to `x-types` package. Change the imports from `x-adapter` to `x-type`.
- Removed `TaggingInfo` type. Use `TaggingRequest` from `@empathyco/x-types` instead.

### Features

- move `Request` types to `x-types` package

## [3.0.0-alpha.94](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.93...@empathyco/x-components@3.0.0-alpha.94) (2022-05-09)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.93](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.92...@empathyco/x-components@3.0.0-alpha.93) (2022-05-06)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.92](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.91...@empathyco/x-components@3.0.0-alpha.92) (2022-05-05)

### Features

- **facets:** expose `clickEvents` as `prop` in filters components using `RenderlessFilter`

## [3.0.0-alpha.91](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.90...@empathyco/x-components@3.0.0-alpha.91) (2022-05-04)

### Features

- add `alt-text` accessibility

## [3.0.0-alpha.90](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.89...@empathyco/x-components@3.0.0-alpha.90) (2022-05-03)

### Features

- **history-queries:** add `MyHistory` component

## [3.0.0-alpha.89](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.88...@empathyco/x-components@3.0.0-alpha.89) (2022-04-29)

### Build System

- **deps:** update eslint-plugin dependencies [(#447)](https://github.com/empathyco/x/pull/447)

## [3.0.0-alpha.88](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.87...@empathyco/x-components@3.0.0-alpha.88) (2022-04-29)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.86](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.85...@empathyco/x-components@3.0.0-alpha.86) (2022-04-19)

### Features

- **eslint:** add `vuejs-accessibility` plugin [(#427)](https://github.com/empathyco/x/pull/427)

## [3.0.0-alpha.85](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.84...@empathyco/x-components@3.0.0-alpha.85) (2022-04-14)

### Features

- extract SessionService to x-utils package

## [3.0.0-alpha.84](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.83...@empathyco/x-components@3.0.0-alpha.84) (2022-04-07)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.83](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.82...@empathyco/x-components@3.0.0-alpha.83) (2022-04-07)

### Code Refactoring

- move DeepPartial type from x-components to x-utils

### Documentation

- activating ready live-examples

## [3.0.0-alpha.82](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.81...@empathyco/x-components@3.0.0-alpha.82) (2022-04-05)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.81](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.80...@empathyco/x-components@3.0.0-alpha.81) (2022-04-05)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.80](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.79...@empathyco/x-components@3.0.0-alpha.80) (2022-04-04)

### Testing

- Restructure files for non global step def [(#382)](https://github.com/empathyco/x/pull/382)

## [3.0.0-alpha.79](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.78...@empathyco/x-components@3.0.0-alpha.79) (2022-04-04)

### Build System

- **deps:** Upgrade Cypress and Vue Cli plugins versions.
  [(#399)](https://github.com/empathyco/x/pull/399)

## [3.0.0-alpha.78](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.77...@empathyco/x-components@3.0.0-alpha.78) (2022-04-04)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.77](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.76...@empathyco/x-components@3.0.0-alpha.77) (2022-04-01)

### Code Refactoring

- move `object` utils from `x-components` to `x-utils`

## [3.0.0-alpha.76](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.75...@empathyco/x-components@3.0.0-alpha.76) (2022-04-01)

### Code Refactoring

- move `NonPrimitive`, `Primitive` and `AnyFunction` types from `x-components` to `x-utils`

### Documentation

- fix links and update repository information and development setup for `x-components`
  [(#394)](https://github.com/empathyco/x/pull/394)

## [3.0.0-alpha.75](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.74...@empathyco/x-components@3.0.0-alpha.75) (2022-03-31)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.74](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.73...@empathyco/x-components@3.0.0-alpha.74) (2022-03-31)

### Bug Fixes

- **base-currency:** format preference goes prop to be injected by default

## [3.0.0-alpha.73](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.72...@empathyco/x-components@3.0.0-alpha.73) (2022-03-24)

### Features

- **history-queries:** add toggle to enable/disable the history queries

## [3.0.0-alpha.72](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.71...@empathyco/x-components@3.0.0-alpha.72) (2022-03-23)

### Documentation

- Update documentation to differentiate integration from development

## [3.0.0-alpha.71](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.70...@empathyco/x-components@3.0.0-alpha.71) (2022-03-23)

### Testing

- E2E tests maintenance [(#371)](https://github.com/empathyco/x/pull/371)

## [3.0.0-alpha.70](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.69...@empathyco/x-components@3.0.0-alpha.70) (2022-03-21)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.69](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.68...@empathyco/x-components@3.0.0-alpha.69) (2022-03-18)

### Features

- **history-queries:** add `my-history` component

## [3.0.0-alpha.68](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.67...@empathyco/x-components@3.0.0-alpha.68) (2022-03-16)

### Bug Fixes

- prevent node-ipc vulnerability

## [3.0.0-alpha.67](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.66...@empathyco/x-components@3.0.0-alpha.67) (2022-03-11)

### ⚠ BREAKING CHANGES

- Remove `selected` and `previous` logic from related tags.
- Remove `EmpathyRequestRelatedTagsQueryMapper`.

### Features

- move related tags concatenation logic [(#365)](https://github.com/empathyco/x/pull/365)

## [3.0.0-alpha.66](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.65...@empathyco/x-components@3.0.0-alpha.66) (2022-03-09)

### Testing

- **e2e:** Fix E2E tests in Firefox

## [3.0.0-alpha.65](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.64...@empathyco/x-components@3.0.0-alpha.65) (2022-03-08)

### Features

- update typescript

## [3.0.0-alpha.64](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.63...@empathyco/x-components@3.0.0-alpha.64) (2022-03-03)

### Features

- Add `setSnippetConfig` function to the `X` API

## [3.0.0-alpha.63](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.62...@empathyco/x-components@3.0.0-alpha.63) (2022-03-01)

### Build System

- remove `polyfills` support

## [3.0.0-alpha.62](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.61...@empathyco/x-components@3.0.0-alpha.62) (2022-02-28)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.61](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.60...@empathyco/x-components@3.0.0-alpha.61) (2022-02-24)

### Testing

- **e2e:** add `extra-params` scenarios

## [3.0.0-alpha.60](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.59...@empathyco/x-components@3.0.0-alpha.60) (2022-02-24)

### Features

- **facets:** add facets mixin to share logic between components

### Testing

- **e2e:** fix `tagging` using the `mockedAdapter` and replacing `fetch` for `sendBeacon`

## [3.0.0-alpha.59](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.58...@empathyco/x-components@3.0.0-alpha.59) (2022-02-17)

### Features

- **design-system:** add `curated` modifier to the `suggestion`

## [3.0.0-alpha.58](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.57...@empathyco/x-components@3.0.0-alpha.58) (2022-02-16)

### Features

- **scroll:** add scroll data state to the alias API

## [3.0.0-alpha.57](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.56...@empathyco/x-components@3.0.0-alpha.57) (2022-02-16)

### Bug Fixes

- **build:** Fix build side effects to include css.

## [3.0.0-alpha.56](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.55...@empathyco/x-components@3.0.0-alpha.56) (2022-02-15)

### Bug Fixes

- **decorators:** pending `debounced` execution is cancelled when the component is destroyed

## [3.0.0-alpha.55](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.54...@empathyco/x-components@3.0.0-alpha.55) (2022-02-10)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.54](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.53...@empathyco/x-components@3.0.0-alpha.54) (2022-02-09)

### ⚠ BREAKING CHANGES

- **components:** Removed `CollapseFromTop` Animation. Use `animateScale()` instead.
- **components:** Removed `TranslateFromLeft` and `TranslateFromRight` components. Use
  `animateTranslate('left')` and `animateTranslate('right')` instead.

### Features

- **components:** created abstract factory for animations

## [3.0.0-alpha.53](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.52...@empathyco/x-components@3.0.0-alpha.53) (2022-02-08)

### Continuous Integration

- update rollup and plugins version

## [3.0.0-alpha.52](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.51...@empathyco/x-components@3.0.0-alpha.52) (2022-02-07)

### Documentation

- fix multiple broken links

## [3.0.0-alpha.51](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.50...@empathyco/x-components@3.0.0-alpha.51) (2022-02-04)

### Code Refactoring

- change to the top of the wiring the ParamsLoadedFromUrl event.

## [3.0.0-alpha.50](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.49...@empathyco/x-components@3.0.0-alpha.50) (2022-02-04)

### Features

- **design-system:** change curated tag toke values to reuse default ones.

## [3.0.0-alpha.49](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.48...@empathyco/x-components@3.0.0-alpha.49) (2022-02-03)

### Continuous Integration

- release alpha version on every push to main branch

## [3.0.0-alpha.48](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.47...@empathyco/x-components@3.0.0-alpha.48) (2022-02-02)

### ⚠ BREAKING CHANGES

- **facets:** Remove `BaseFilter` component. Use `RenderlessFilter`instead.

### Features

- **design-system:** add curated tags [(#311)](https://github.com/empathyco/x/pull/311)
- **extra-params:** add option to add more extra params using prop in `SnippetConfigExtraParams`
  component
- **facets:** change `NumberRangeFilter` component to use `RenderlessFilter` instead of `BaseFilter`
- update polyfills plugin to work with chunks

## [3.0.0-alpha.47](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.46...@empathyco/x-components@3.0.0-alpha.47) (2022-02-01)

### Features

- **components:** Add `payload` and `metadata` to the `SnippetCallbackExecuted` event payload
- **components:** Allow `BaseResultAddToCart` to use external listeners.
- track PDP add to cart [(#306)](https://github.com/empathyco/x/pull/306)

## [3.0.0-alpha.46](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.45...@empathyco/x-components@3.0.0-alpha.46) (2022-01-24)

### Bug Fixes

- **components:** Fix BaseGrid auto columns CSS. [(#308)](https://github.com/empathyco/x/pull/308)

### Build System

- Fix colors.js dependency issue

## [3.0.0-alpha.45](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.44...@empathyco/x-components@3.0.0-alpha.45) (2022-01-20)

### Features

- **design-system:** allow suggestions to be tags

### Bug Fixes

- **url:** default `extra params` are now properly restored

### Testing

- **e2e:** make `tagging` tests wait for redirection before assertion

## [3.0.0-alpha.44](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.43...@empathyco/x-components@3.0.0-alpha.44) (2022-01-14)

### ⚠ BREAKING CHANGES

- **components:** `SlidingPanel` buttons do not have the round variant set by default.

### Features

- **components:** add `buttonClass` prop in `SlidingPanel`
- **components:** add Result Rating component

### Bug Fixes

- **design-system:** Fix some style issues and add two missing utilities
- **identifier-results:** Fix default plugin config.
  [(#296)](https://github.com/empathyco/x/pull/296)
-

## [3.0.0-alpha.43](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.42...@empathyco/x-components@3.0.0-alpha.43) (2022-01-06)

### Features

- **components:** Add icons for Arrows UP DOWN LEFT and RIGHT.
  [(#295)](https://github.com/empathyco/x/pull/295)

## [3.0.0-alpha.42](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.41...@empathyco/x-components@3.0.0-alpha.42) (2022-01-05)

### Features

- **design-system:** Add more utility classes.
- **design-system:** Add `Grid2RowsIcon` component

### Bug Fixes

- **design-system:** Fix grid styles to stretch cells.
- **design-system:** Fix Sliding Panel styles.

## [3.0.0-alpha.41](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.40...@empathyco/x-components@3.0.0-alpha.41) (2022-01-03)

### Features

- **next-queries:** add isCurated property

## [3.0.0-alpha.40](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.39...@empathyco/x-components@3.0.0-alpha.40) (2021-12-29)

### Features

- **tagging:** add new `SearchTaggingReceived` event for tracking the query

### Bug Fixes

- **components:** `SlidingPanel` can now disable the resetting scroll …
  [(#286)](https://github.com/empathyco/x/pull/286)
- **related-tags:** clear selected related tags when user changes extra params
- **search:** batch state reset calls after search.request parameter changes
  [(#283)](https://github.com/empathyco/x/pull/283)
- **search:** next page is now requested if it has less than the page size results.
  [(#284)](https://github.com/empathyco/x/pull/284)

## [3.0.0-alpha.39](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.38...@empathyco/x-components@3.0.0-alpha.39) (2021-12-22)

### Features

- **design-system:** Add bottom variant to `x-shadow` utility in the Design System

### Bug Fixes

- Fix multiple issues.

## [3.0.0-alpha.38](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.37...@empathyco/x-components@3.0.0-alpha.38) (2021-12-22)

### Features

- **design-system:** Add new color tokens. [(#275)](https://github.com/empathyco/x/pull/275)
- **test:** refactor base tests to cypress component testing
- **x-plugin:** Add selected sort [(#274)](https://github.com/empathyco/x/pull/274)

### Bug Fixes

- **components:** Fix infinite scroll not working in Android Chrome.
  [(#277)](https://github.com/empathyco/x/pull/277)
- **search:** rows and start parameters calculations moved from getter to action to avoid multiple
  requests

## [3.0.0-alpha.37](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.36...@empathyco/x-components@3.0.0-alpha.37) (2021-12-15)

### Features

- **scroll:** remove animations on pending element to scroll
- **tagging:** Include 'location' parameter to track result events.
  [(#273)](https://github.com/empathyco/x/pull/273)
-

## [3.0.0-alpha.36](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.35...@empathyco/x-components@3.0.0-alpha.36) (2021-12-15)

### Build System

- Load PostCSS plugins from rollup build [(#272)](https://github.com/empathyco/x/pull/272)

### Testing

- **e2e:** fix tagging tests [(#270)](https://github.com/empathyco/x/pull/270)

## [3.0.0-alpha.35](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.34...@empathyco/x-components@3.0.0-alpha.35) (2021-12-14)

### Features

- **components:** fix 'BaseRating' component styles
  [(#264)](https://github.com/empathyco/x/pull/264)
- **plugin:** move alias creation from created hook to beforeCreated
- **tagging:** track pending query
- **tagging:** track result click events
- **tagging:** track the 'UserClickedResultAddToCart' event in tagging
- **wiring:** add force and cancel support to debounce and throttle wire operators. Update rxjs to

### Bug Fixes

- **components:** Export missing layout components
- **extra-params:** prevent callbacks option from the snippet config to be taken as extra params

### Testing

- **e2e:** make url tests intercept tracking and wait for each request

### Documentation

- add guide for integrating X Interface into an existing website
- change h1 to be h2

## [3.0.0-alpha.34](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.33...@empathyco/x-components@3.0.0-alpha.34) (2021-12-03)

### Features

- **search-box:** focus search input after clicking clear search button
- **tagging:** move `origin` from `request.getter` to `fetchAndSave.action`
- **url:** set `origin` when navigating

### Documentation

- Remove docusaurus headers

## [3.0.0-alpha.33](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.32...@empathyco/x-components@3.0.0-alpha.33) (2021-11-30)

### Features

- **related-tags:** add `isCurated` property to related tags
- **search:** change `saveOriginWire` wire from `SelectedRelatedTagsChanged` to
  `UserPickedARelatedTag` [(#254)](https://github.com/empathyco/x/pull/254)
- **utils:** now `origin` only requires the `feature`

## [3.0.0-alpha.32](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.31...@empathyco/x-components@3.0.0-alpha.32) (2021-11-29)

### ⚠ BREAKING CHANGES

- **storage-service:** `StorageService` has been renamed to `BrowserStorageService`.

### Features

- **components:** Add `GlobalXBus `component
- **components:** add `SnippetCallbacks` component
- **storage-service:** Rename `StorageService` to `BrowserStorageService`

### Bug Fixes

- **tagging:** now removing the session clears the session from the storage

### Build System

- update jest dependencies

## [3.0.0-alpha.31](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.30...@empathyco/x-components@3.0.0-alpha.31) (2021-11-25)

### Features

- **design-system:** add identifier result in suggestion component
- **identifier-results:** add extra params in the x-module
- **tagging:** `track` query
- **tagging:** add feature hardcoded values

### Testing

- **e2e:** Reduce command timeout and number of retries.
- **e2e:** reorder mocked responses

### Documentation

- add new static docs.

## [3.0.0-alpha.30](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.29...@empathyco/x-components@3.0.0-alpha.30) (2021-11-22)

### Features

- **components:** add `LocationProvider` component
- **components:** replace `BaseEventButton` for a html button
- **identifier-results:** add query origin in the identifier results search
- remove x installer from router hooks
- **scroll:** add `MainScroll` and `MainScrollItem`
- **scroll:** add empty `XModule`
- **scroll:** ignore first visible element when it is also the first one observed
- **scroll:** move scroll related components to the `Scroll` `XModule`
- **search:** add `SearchTaggingChanged` emitter and save coming `queryTagging` from the search
  response
- **tagging:** add `SessionService`
- update `Tagging` model
- **x-plugin:** Make XPluginMixin to add the component `location` to metadata.

### Bug Fixes

- **identifier-results:** provide resultClickExtraEvents so BaseResultLink emits them when clicked

### Testing

- **e2e:** add typing to e2e stubs
- **e2e:** complete filter tests scenarios
- **e2e:** fix invalid identifier results data test selector
- **e2e:** remove sliding panel test wait
- **search:** redefine old search tests

## [3.0.0-alpha.29](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.28...@empathyco/x-components@3.0.0-alpha.29) (2021-11-09)

### Features

- **url:** set sort values and read them from the url

## [3.0.0-alpha.28](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.27...@empathyco/x-components@3.0.0-alpha.28) (2021-11-03)

### Features

- **components:** add new fixed header and aside layout
- **design-system:** Add Design System Message and Progress Bar components
- **extra-params:** Add support to `UrlHandler` for handling `extra-params`
- **search:** add Redirection and AutoProgressBar components
- update x-components browserslist
- **x-plugin:** Update Alias API with `noResults`, `redirections` and `partialResults`

### Bug Fixes

- **facets:** now service uses only the first filter entity to update the facets.
- **url:** Fix URL clear query issue
- **x-plugin:** fix no results message flash on load

### Code Refactoring

- **design-system:** Refactor Design System View

### Testing

- **e2e:** fix sort intercepted request

## [3.0.0-alpha.27](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.26...@empathyco/x-components@3.0.0-alpha.27) (2021-10-25)

### ⚠ BREAKING CHANGES

- Slots that are created using properties like the `modelName` or the `id` of different objects, now
  are named using the kebab-case version of those values. This affects the following components:
  `BaseGrid`, `Facets` and `SelectedFiltersList`. Examples: `<template #Result="{ ... }">` now is
  `<template #result="{ ... }">` `<template #NextQueriesGroup="{ ... }">` now is
  `<template #next-queries-group="{ ... }">` `<template #hierarchical_category="{ ... }">` now is
  `<template #hierarchical-category="{ ... }">`

### Features

- change all dynamic slots to kebab-case
- **components:** move `maxItemsToRender` prop to `BaseSuggestions`. Add `maxItemsToRender` prop to
  `Recommendations`.
- **plugin:** minimise initial duplicated requests using debounce
- **url:** refactor module logic moving some logic to UrlHandler Component
- **url:** syncronize url and state with the facets and remove query from facets module
- **url:** syncronize url and state with the page

### Code Refactoring

- **url:** change `updateUrl` action to be class

### Testing

- **e2e:** use main layout in mocked tests

### Styling

- add pre-commit hooks to run eslint and prettier

### Documentation

- fix components documentation export
- Fix components documentation markdown

## [3.0.0-alpha.26](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.25...@empathyco/x-components@3.0.0-alpha.26) (2021-09-23)

### Features

- **design-system:** add tokens for non matching part of suggestion
- **url:** set the related tags from the url in the store and viceversa
- **url:** syncronize url and state with the page

### Code Refactoring

- **facets:** fix facets performance issues

### Styling

- format with prettier and avoid fixing code while linting

## [3.0.0-alpha.25](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.24...@empathyco/x-components@3.0.0-alpha.25) (2021-09-22)

### Features

- **components:** Add `TranslateFromLeft` and `CrossFade` animations.
- **url:** syncronize url and state with the query

### Code Refactoring

- use `NamedModel` generic parameter to better type models

## [3.0.0-alpha.24](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.23...@empathyco/x-components@3.0.0-alpha.24) (2021-09-20)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.23](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.22...@empathyco/x-components@3.0.0-alpha.23) (2021-09-20)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.22](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.21...@empathyco/x-components@3.0.0-alpha.22) (2021-09-17)

### Features

- **design-system:** add utilities
- **url:** Add an action to save from url to the store.
- **url:** add new URL Manager component

### Testing

- **partial-results:** mock adapter for partial results e2e tests

## [3.0.0-alpha.21](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.20...@empathyco/x-components@3.0.0-alpha.21) (2021-09-15)

### Features

- **design-system:** add `Shadow` component
- **e2e:** mock adapter for query suggestions tests
- export store utils

### Bug Fixes

- **design-system:** fix typo. Increase `gap` and `padding` tokens up to 10. Add class for list item
  flex none

## [3.0.0-alpha.20](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.19...@empathyco/x-components@3.0.0-alpha.20) (2021-09-15)

### Features

- **no-suggestions:** Remove `no-suggestions` module.
- **search:** save `Redirection`'s entities

## [3.0.0-alpha.19](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.18...@empathyco/x-components@3.0.0-alpha.19) (2021-09-13)

### Bug Fixes

- Fix recommendations `setParams` wire. Export `LIST_ITEMS_KEY`.

## [3.0.0-alpha.18](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.17...@empathyco/x-components@3.0.0-alpha.18) (2021-09-10)

### ⚠ BREAKING CHANGES

- **facets:** Rename `Filters` component to `FiltersList`.
- **facets:** Remove `MultiSelectFilters` component. Filters are multi-select by default. Apply the
  `SingleSelectModifier` using the `FilterEntityFactory` to make the desired `Facet` single select.
- **facets:** Refactor `HierarchicalFilter.children` field. Now, this field is list of the
  `Filter.ids` of the children filter. All `HierarchicalFilter`s are flattened in the
  `Facet.filters` list.
- **facets:** Remove `facets` prop in the `Facets` component to provide `Facets` to the state. Use
  the `FacetsProvider` component instead.
- **facets:** Remove `UserChangedSelectedFilters` event from `Facets` component. Use
  `FacetsProvider` component instead.
- **facets:** Remove `UserClickedClearFacetFilters` event. `UserClickedClearAllFilters` is emitted
  instead. Its payload is now list of `Facet.id`s.
- **facets:** Rename `UserClickedFacetAllFilter` event to `UserClickedAllFilter`. Its payload is now
  list of `Facet.id`s.
- **facets:** Remove `BackendFacetsChanged` event. Use `FacetsChanged` event instead.
- **facets:** Remove `BackendFacetsProvided` event. Use `FacetsGroupProvided` instead.
- **facets:** Remove `FrontendFacetsChanged` event. Use `FacetsGroupProvided` instead.
- **facets:** Remove `FacetMultiSelectChanged` event. `Filter`s are multi-select by default. Apply
  the `SingleSelectModifier` using the `FilterEntityFactory` to make the desired `Facet` single
  select.
- **facets:** Change `UserModifiedEditableNumberRangeFilter` payload. Now it is the
  `EditableNumberRangeFilter` filter with the new range value.

### Features

- **animations:** add new `TranslateFromRight` animation
- **design-system:** add `SingleColumnLayout` component.
- **design-system:** add lists background colors to Design System
- **facets-next:** move HierarchicalFilter component to new `facets-next` x-module
- **facets:** remove old `facets` X Module and replace by `facets-next`.
- **mixin:** add origin injection in the mixin and the bus
- **next-queries:** add `NextQueriesList` component.
- **search:** add origin to the request
- **spellcheck:** add spellchecked query to Alias API
- **url:** add `url` x-module config. [(#129)](https://github.com/empathyco/x/pull/129)
- **url:** add new events
- **url:** add url module state, urlParams getter and its emitter

### Bug Fixes

- **design-system:** fix issues with components height and layout
- **popular-searches:** fix popular searches and query suggestions canceling requests.

### Testing

- **e2e:** mock adapter for identifier results

## [3.0.0-alpha.17](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.16...@empathyco/x-components@3.0.0-alpha.17) (2021-08-26)

### Features

- **facets-next:** add all remaining components to Facets Next X-Module
- **next-queries:** add extra params in the request
- **popular-searches:** add extra params
- **query-suggestions:** add new extra params in the request
- **recommendations:** recommendations extra params and state reset on change.
- **related-tags:** add new extra params in the request
- **search:** add extra params to search module

### Testing

- **e2e:** mock search-box e2e tests

## [3.0.0-alpha.16](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.15...@empathyco/x-components@3.0.0-alpha.16) (2021-08-24)

### Features

- **extra-params:** add new renderless extra params component
- **extra-params:** add new snippet extra params component
- **facets-next:** add `AllFilter`, `BaseFilter` and `EditableNumberRangeFilter` components to
  `facets-next` x-module.
- **facets-next:** add `Facets` component to `facets-next` x-module
- **facets-next:** add `FacetsProvider` component
- **facets-next:** add `SimpleFilter`, `HierarchicalFilter`, `NumberRangeFilter`, `RenderlessFilter`
  and `Filters` components to the `facets-next` x-module.

### Testing

- **facets-next:** add missing service tests

## [3.0.0-alpha.15](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.14...@empathyco/x-components@3.0.0-alpha.15) (2021-08-20)

### Features

- **extra-params:** add `ExtraParams` component
- **extra-params:** add module
- **facets-next:** add facets to the state and facets getter
- modify search function in XAPI to open X
- **facets-next:** Add `FacetsService`
- **facets-next:** add wiring. add new `wireService` and `wireServiceWithoutPayload` wires
  factories.
- **url:** add new empty module

### Testing

- **e2e:** mock adapter on popular searches requests
- **e2e:** move stubs creation within the test itself and rewrite mocking features

## [3.0.0-alpha.14](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.13...@empathyco/x-components@3.0.0-alpha.14) (2021-08-11)

### ⚠ BREAKING CHANGES

- **components:** Remove `hideIntegerDecimals` from `currency-formatter` util, `base-currency`
  component.
- **facets-next:** Rename `EmpathyFilterMapper` to `EmpathyFacetFilterMapper`. Response filter
  mappers now map the API value in the `id` filters property. `EmpathyHierarchicalFacetMapper` now
  flattens and stores all the filters in the `filter` property. `EmpathyHierarchicalFacetMapper` now
  only maps filters ids in `HierarchicalFilter` children. Bump up `@empathyco/x-types` major version
  in `@empathyco/x-adapter`.

### Features

- **components:** add option to hide decimals if the number to format is an integer in
  `currencyFormatter` `format` option.
- **facets-next:** add entity filter modifiers
- **facets-next:** add support for the new search types in search adapter

### Testing

- **e2e:** mock adapter on next queries requests
- **e2e:** mock all the e2e requests of Next Queries

## [3.0.0-alpha.13](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.12...@empathyco/x-components@3.0.0-alpha.13) (2021-08-05)

### Build System

- upgrade x-translations dependencies

## [3.0.0-alpha.12](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.11...@empathyco/x-components@3.0.0-alpha.12) (2021-08-05)

### Features

- **facets-next:** add `EditableNumberRangeFilterEntity`
- **facets-next:** add `HierarchicalFilterEntity`
- **facets-next:** add `RawFilterEntity`

## [3.0.0-alpha.11](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.10...@empathyco/x-components@3.0.0-alpha.11) (2021-08-03)

### Features

- **facets-next:** add `SimpleFilterEntity`

### Bug Fixes

- **animations:** disable leaving elements listening to click events

### Build System

- Update TypeScript to 4.3.5.Update TSLib to 2.3.5.

## [3.0.0-alpha.10](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.9...@empathyco/x-components@3.0.0-alpha.10) (2021-07-29)

### Features

- **facets-next:** add module

### Build System

- use 2 different versions of search-types

## [3.0.0-alpha.9](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.8...@empathyco/x-components@3.0.0-alpha.9) (2021-07-29)

### Bug Fixes

- **banners:** fix repeated banners and promoted on page load
- **directives:** change `infinite-scroll` threshold to avoid decimals bug in `Chrome`

## [3.0.0-alpha.8](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.7...@empathyco/x-components@3.0.0-alpha.8) (2021-07-28)

### Bug Fixes

- **promoted:** fix name export of PromotedsList component

## [3.0.0-alpha.7](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.5...@empathyco/x-components@3.0.0-alpha.7) (2021-07-27)

### Features

- **search:** add `BannersList` and `PromotedsList` components

### Bug Fixes

- **design-system:** Fix padding in Input Group Line variant

### Code Refactoring

- **design-system:** rename `tokens` to use `style-dictionary`

### Testing

- **e2e:** stub 'adapter.getTopRecommendations` calls

## [3.0.0-alpha.6](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.5...@empathyco/x-components@3.0.0-alpha.6) (2021-07-20)

**Note:** Version bump only for package @empathyco/x-components

## [3.0.0-alpha.5](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.4...@empathyco/x-components@3.0.0-alpha.5) (2021-07-20)

### Continuous Integration

- Fix publishing in x-components. Normalize build scripts.

## [3.0.0-alpha.4](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.3...@empathyco/x-components@3.0.0-alpha.4) (2021-07-15)

### Testing

- **component:** configure Cypress component testing

## [3.0.0-alpha.3](https://github.com/empathyco/x/compare/@empathyco/x-components@3.0.0-alpha.2...@empathyco/x-components@3.0.0-alpha.3) (2021-07-14)

### Features

- **design-system:** add scroll-to-top slot in Layout
- **search:** add `Promoted` component
- **search:** add Banner component

### Bug Fixes

- **components:** make column picker & grid components listen to only `ColumnsNumberProvided` event
  to fix incorrect columns number on re-mounts
- **directives:** `InfiniteScroll` now works properly in Safari and with html or body as containers
- **search:** clean sort value after accept new query

### Documentation

- **query-suggestions:** adapt examples to edocs guidelines
- **related-tags:** adapt to eDocs guidelines

### Testing

- enable e2e test and fix tests

## 3.0.0-alpha.2 (2021-06-30)

### Features

- **facets:** add `click:show-more` & `click:show-less` events to the `SlicedFilters` component.

### Bug Fixes

- **components:** `StaggeringTransitionGroup` elements now are positioned correctly in scroll
  containers

## 3.0.0-alpha.1 (2021-06-30)

### Features

- **components:** Add `@XEmit` decorator
- **device:** Add `device` module
- **device:** add `DeviceDetector` component
- **x-installer:** make `SnippetConfig` object available for all components
- **x-plugin:** Remove `XConfig`

### Bug Fixes

- **design-system:** solve `Safari` `gap` issues

### Testing

- **e2e:** add test for spellcheck component

### Documentation

- **search-box:** update props and bindings table style and avoid warning block auto-formatting

### Styling

- format entire project

## 3.0.0-alpha.0 (2021-06-22)

### ⚠ BREAKING CHANGES

- **design-system:** Design system styles have now to be imported from
  `@empathy/x-components/design-system` instead of `@empathy/x-components/css`

### Features

- **components:** add new `BaseIdPanelToggleButton` and `BaseIdPanelToggle` components

### Testing

- **e2e:** add identifier results tests

### Code Refactoring

- **design-system:** rename `styles` folder to `design-system`

## 2.1.0-alpha.1 (2021-06-16)

### Features

- **components:** change the render conditions in the `Layout` component
- **design-system:** add `x-button--ghost-start` and `x-button--ghost-end` modifiers to
  `x-button--ghost` variant
- **design-system:** add `x-dropdown` size variants
- **design-system:** add more values to the `x-list` variants
- **design-system:** fix the issue with the `x-tag` and `x-filter` in the selected filters
- **empathize:** add `isOpen` to store state and expose through the Alias API
- **facets:** add `isSelected` binding to the `AllFilter` component slot

### Bug Fixes

- **components:** emit initial default value in the `ColumnPicker` mixin
- **design-system:** fix the stroke and the text decoration in the typography
- **facets:** `isNewQuery` utility was returning false when only one query was empty
- **facets:** new label slot inside the `Hierarchical Filter` children
- **utils:** add missing exports to barrel

### Documentation

- **search-box:** remove values column in props generated table in component doc

### Testing

- **e2e:** add partial results tests

## 2.1.0-alpha.0 (2021-06-14)

### Features

- **components:** add `AnimateWidth` animation component
- **design-system:** add `SlidingPanel` default CSS and tokens
- **design-system:** add `x-scroll` component and tokens
- **design-system:** add Design System classes for the picture image fallback and placeholder
- **design-system:** add Design System icons
- **design-system:** add Direction Border and Padding List variants
- **design-system:** add icons to the Design System view
- **design-system:** add Layout component and Design System Layout component
- **design-system:** add list design tokens
- **design-system:** add new typography variants
- **design-system:** add option list tokens
- **design-system:** add `x-grid` Design System tokens
- **design-system:** add `x-result` Design System tokens
- **design-system:** improve `x-icon` token
- **design-system:** add `x-row` and `x-row-item` tokens
- **design-system:** add `x-picture` Design System tokens
- **facets:** add `SortedFilters` component
- **components:** change `NoElement` component to be not functional
- **components:** add `BaseResultPlaceholderImage` and `BaseResultFallbackImage`

### Bug Fixes

- **components:** fix `SlidingPanel` buttons were blocking clicks while invisible
- **facets:** fix issue with hierarchical filters with no children
- **search:** fix infinite scroll issues when filtering

### Testing

- **e2e:** adapt `empathize` tests to cucumber
- **e2e:** update Cypress to 7.4.0

### Continuous Integration

- **CI:** update package-lock

### Build System

- **dependencies:** update `search-adapter` version

### Documentation

- **search-box:** update `SearcInput` component documentation
- **search-box:** update `ClearSearchInput` documentation
- **search-box:** update `SearchButton` documentation
- **build:** avoid creating Methods section in components documentation

### Code Refactoring

- **components:** refactor `CollapseFromTop` animation to use only transformations

## 2.0.0 (2021-06-03)

### Features

- **design-system:** add `x-sliding-panel` tokens
- **design-system:** add design system icons
- **design-system:** add `x-list`and variants tokens
- **design-system:** add `x-option-list` and variants tokens
- **design-system:** add `x-row` and `x-row-item` tokens
- **design-system:** add `x-picture` tokens
- **facets:** add `SortedFilters` component
- **no-element:** change `NoElement` component to be not functional

### Bug Fixes

- **search:** fix infinite scroll issues when filtering

### Testing

- **e2e:** adapt `empathize` tests to cucumber
- **e2e:** update Cypress to 7.4.0

### Build System

- **dependencies:** update `search-adapter` version

### Documentation

- **search:** update search input component documentation
- **components:** avoid creating Methods section in components documentation

## 2.0.0-alpha.13 (2021-05-28)

### Features

- **design-system:** add `input-group` variants
- **design-system:** add `justified` variant to `x-filter` component
- **design-system:** add `x-button` css class in the necessary elements
- **design-system:** add `x-filter` tokens and CSS
- **design-system:** add `x-suggestion` design tokens
- **design-system:** add `x-tag` variants tokens and CSS styles
- **design-system:** add default `x-facet` tokens and CSS and `x-icon` variants
- **design-system:** add dropdown design tokens
- **design-system:** add input default tokens and CSS
- **design-system:** add input variants tokens and CSS
- **design-system:** add tags default tokens and CSS
- **design-system:** add the `.x-input` class to the XComponents where necessary
- **design-system:** add x-facet variants tokens and CSS styles
- **design-system:** add x-tag css class in the necessary elements
- **design-system:** refactor styles folder structure
- **design-system:** add `hierarchical` variant to `x-filter`
- **facets:** add support for optional hierarchical filter children prop
- **search:** add infinite scroll to `ResultsList` component
- **search:** Add `page` and `pageSize` properties with its mutations.
- **search:** update search getter in order to use the new page and pageSize properties of the
  module

### Bug Fixes

- **components:** fix `transform` transition in `FadeAndSlide` animation component
- **design-tokens:** fix editable tokens not being displayed in view correctly

### Build System

- **design-system:** add the Rollup configuration to build the CSS files of the Design System

### Documentation

- **components:** improve the way to show slot bindings data in the components documentation

### Testing

- remove old tests

## 2.0.0-alpha.12 (2021-05-06)

### Features

- **components:** add an overlay layer to `BaseModal` component listening to click events outside
  the modal to close it
- **recommendations:** add scopedSlot `layout` to `Recommendations` component

### Bug Fixes

- **components:** fix `FadeAndSlide` and `StaggeredFadeAndSlide` animations

### Testing

- **e2e:** Add multiselect-filters test

## 2.0.0-alpha.10 (2021-05-03)

### Features

- **contributing-guide:** Add contributing guide
- **design-system:** add base tokens
- **design-system:** add Button variations tokens and CSS
- **design-system:** add default button design tokens and styles
- **design-system:** add Design System view as showcase
- **directives:** add `InfiniteScroll` directive
- **directives:** add barrel file in `directives` folder and export them in `src`
- **facets:** add `RenderlessFilter` component
- **facets:** change `BaseFilter` to `RenderlessFilter` in `HierarchicalFilter` component
- **facets:** make `SimpleFilter` component use `RenderlessFilter`, exposing the option of changing
  the default button.
- **facets:** use the new decorators `inject` and `provide` in the filters components
- **x-installer:** add option to install asynchronous Vue plugins

### Bug Fixes

- **tests:** enable new scenario in `querySuggestions` and fix `isInQuerySuggestions` method

### Build System

- **dependencies:** update `search-adapter` and `search-types` versions
- **package.json:** update fixed dependencies (package-lock.json) and fix eslint version to minor

### Testing

- **e2e:** add different possible combinations for filters-search components
- **e2e:** add new sort tests
- **e2e:** e2e test for exclude-filters-with-no-results component

### Documentation

- **tests** add tests docs in contributing documentation about factory functions and components
  wrappers
- **xcomponents:** add documentation about events emitted by components

## 2.0.0-alpha.9 (2021-04-13)

### Bug Fixes

- **facets:** Emit the `SelectedFiltersChanged` event when the user deselects the last filter

## 2.0.0-alpha.8 (2021-04-13)

### Bug Fixes

- **facets:** Avoid emitting the `SelectedFiltersChanged` event when facets change for the second
  time.

## 2.0.0-alpha.7 (2021-04-07)

### Features

- **components:** add `BaseColumnPickerList` component
- **components:** add `BaseVariableColumnGrid` component
- **components:** add `BaseIdScroll` component
- **components:** add `BaseMainScroll` component
- **decorators:** add `@XProvide` and `@XInject` decorators
- **facets:** add `ExcludeFiltersWithNoResults` component
- **facets:** add `EditableNumberRangeFilter` component
- **facets:** add new events, wiring, and action to keep backend filters selected state
- **facets:** add the option to init the `frontendFacets` via prop in the `Facets` component
- **facets:** add wiring and store logic in facets module to support `EditableNumberRangeFilter`
- **grid:** add `BaseColumnPickerDropdown` component
- **history-queries:** modify history-queries to accept new config and show all the elements in
  store.
- **scroll:** add new `BaseScrollToTop` component
- **scroll:** add new `BaseScroll` component
- **search:** add `PartialResultsList` component
- **search:** add `SortDropdown` component
- **search:** add new `PartialQueryButton` component
- **search:** add new `SortList` component
- **search:** add store logic & wiring to support sorting results
- **tagging:** add basic tagging x-module
- **x-plugin:** add `initialXModules` to `XPluginOptions` to register `XModules` manually when
  installing the plugin

### Code Refactoring

- **animations:** rename animations to fit BEM
- **decorators:** tidy decorators splitting the bus decorators from the state decorators
- **facets:** move filter components inside the facets module

### Testing

- **e2e:** fix e2e `SlidingPanel` tests
- **e2e:** add tests scenarios for sort dropdown and list
- **e2e:** column pickers tests refinement
- **e2e:** fix relative imports paths
- **e2e:** fix setting related tags max items to render in sliding panel view
- **e2e:** add test for `BaseFiltersSearch`
- **e2e:** add test for `BaseColumnPickerList` and dropdown
- **e2e:** add tests for `SlidingPanel` component

## 2.0.0-alpha.6 (2021-03-16)

### ⚠ BREAKING CHANGES

- **facets:** Filters which have selected property now extends from BooleanFilter

### Features

- **facets:** update search-types and search-adapter to allow EditableNumberRangeFilters
- **search:** add `ResultsList` component
- **search:** add `Spellcheck` component
- **search:** add `SpellcheckButton` component
- **search:** add `totalResults` property to the search module state and to the alias API

### Bug Fixes

- **components:** `EventsModalOpen`, `IdModalOpen` components can now contain HTML elements inside.
  Disable page scroll when modals are open. Close modals when either clicked out of them or focus is
  lost

### Testing

- **e2e:** add tests for `BaseKeyboardNavigation` component
- **e2e:** add tests for `BaseResultImage` component

### Build System

- **dependencies:** update `@vue-cli` dependencies to 4.5.x

### Code Refactoring

- add `scoped` attribute to `<style>` to components that were missing it

## 2.0.0-alpha.5 (2021-03-08)

### Build System

- fix publish directory

## 2.0.0-alpha.4 (2021-03-08)

### Features

- **animations:** added z-index within staggered animations styles
- **base-components:** add `base-id-modal`, `base-id-modal-open` and `base-id-moda-close` components
- **base-grid:** add base-grid component
- **components:** add `BaseDropdown` component.
- **components:** add mixing `CollapseWidth` component export
- **facets:** add new filter to deselect the filters if the query has changed
- **facets:** facets split in backend and frontend facets
- **filters:** renders selected filters from state and exposes slots to customize it
- **search:** remove search results getter and replace the access to them with the State decorator
- **search-module:** Add banners an promoteds in store.

### Bug Fixes

- **history-queries:** replace last query, if the last word of it is refined in the new query

### Performance Improvements

- **e2e:** avoid opening new browser instances to speed up e2e tests

### Code Refactoring

- **e2e:** homogenise and standardise common-steps and test cases
- **x-plugin:** extract `XComponentAliasAPI` logic to separate file and improve aliases generation

### Testing

- **e2e:** add next-queries e2e tests
- **e2e:** add test for base event modal
- **e2e:** related tags e2e tests

### Build System

- improve process deleting the temporally directories

## 2.0.0-alpha.3 (2021-02-12)

### ⚠ BREAKING CHANGES

- **currency-formatter:** remove `CurrencyOptions` from `XConfig` and its default value from
  `DEFAULT_X_CONFIG`, remove `ConfigCurrencyChanged` event from `XEventsTypes` and remove `currency`
  property from `SnippetConfig`.
- **exports:** Rename some wires due to collisions between other exported members (i.e.
  actions/getters): `facets` -> `setFacets` to `setFacetsWire`, `toggleSimpleFilter` to
  `toggleSimpleFilterWire`, `toggleHierarchicalFilter` to `toggleHierarchicalFilterWire`,
  `toggleNumberRangerFilter` to `toggleNumberRangerFilterWire`, `clearFacetsSelectedFilters` to
  `clearFacetsSelectedFiltersWire`, `clearFacetSelectedFilters` to `clearFacetSelectedFiltersWire`
  and `clearSelectedFilters` to `clearSelectedFiltersWire`. `history-queries` ->
  `loadHistoryQueriesFromBrowserStorage` to `loadHistoryQueriesFromBrowserStorageWire`.
  `next-queries` -> `fetchAndSaveNextQueries` to `fetchAndSaveNextQueriesWire` and
  `setQueryFromLastHistoryQuery` to `setQueryFromLastHistoryQueryWire`. `query-suggestions` ->
  `fetchAndSaveSuggestions` to `fetchAndSaveSuggestionsWire` and `cancelFetchAndSaveSuggestions` to
  `cancelFetchAndSaveSuggestionsWire`. `related-tags` -> `fetchAndSaveRelatedTags` to
  `fetchAndSaveRelatedTagsWire`, `cancelFetchAndSaveRelatedTags` to
  `cancelFetchAndSaveRelatedTagsWire` and `toggleRelatedTag` to `toggleRelatedTagWire`. `search` ->
  `fetchAndSaveSearchResponse` to `fetchAndSaveSearchResponseWire` and
  `cancelFetchAndSaveSearchResponse` to `cancelFetchAndSaveSearchResponseWire`.

Rename exports of `getters` named `request` to `moduleName` + `Request` due to collisions between
modules. Rename `ClearFilters` class to `ClearSelectedFilters`.

### Features

- **e2e test for recommendations components:** e2e test for recommendations component
- **e2e testing for query-suggestions component:** e2e testing for query-suggestions component
- **facets:** add an option to set the state facets via prop
- **facets:** add renderableFacets prop to Facets component to filter rendered facets
- **facets:** support receiving facets containing selected filters in `Facets.vue`
- **related tags:** added related tags config to set maximum number of items to render

### Styling

- **getters:** rename getters name adding .getter at the end

### Code Refactoring

- **currency-formatter:** extract currency format logic from `base-currency.vue` to
  `currency-formatter` utility
- **exports:** add missing actions and getters exports

### Testing

- **default-tests:** Disabled some of old E2E tests
- **history queries:** e2e test history queries

## 2.0.0-alpha.2 (2021-01-20)

### Bug Fixes

- **facets:** add missing `SelectedFilters` component export

## 2.0.0-alpha.1 (2021-01-19)

### ⚠ BREAKING CHANGES

- **base-components:** `BaseModalContainer` has been split into 2 new components: `BaseEventsModal`,
  which acts like the old component, but with the `eventToEmitOnClose` prop renamed to
  `bodyClickEvent`. `BaseModal` now acts as dumb modal that receives its open state via props.
  `BaseCloseButton` has been renamed to `BaseEventsCloseButton` `BaseOpenButton` has been renamed to
  `BaseEventsOpenButton` Events have been renamed: `UserOpenedX` -> `UserClickedOpenX`,
  `UserClosedX` -> `UserClickedCloseX`

### Features

- **animations:** add `CollapseWidth` animation
- **base-components:** add `BaseRating` component
- **base-components:** add `BaseRatingFilterLabel` component
- **base-components:** add `BaseModal` and `BaseEventsModal` components
- **base-components:** add `BasePriceFilterLabel` component
- **facets:** add `selectedFilters` binding for each slot and facet in `Facets` component
- **facets:** add `clearSelectedFilters` wire in `UserAcceptedAQuery` event
- **facets:** add `SelectedFilters` component which renders the selected filters

### Bug Fixes

- **plugin:** fix types to allow overriding parts of the store

### Code Refactoring

- **animations:** extract mixin from `CollapseHeight` and `CollapseWidth` animations
- **components/filters:** reorganize components/filters directory

### Testing

- **e2e:** implement search-box test scenarios
- **e2e:** update cypress version
- **e2e:** refine search-box tests

## 2.0.0-alpha.0 (2020-12-29)

### ⚠ BREAKING CHANGES

- rename actions in several modules: Popular searches `getSuggestions` → `fetchSuggestions`. Query
  suggestions: `getAndSaveSuggestions` → `fetchAndSaveSuggestions`, `getSuggestions` →
  `fetchSuggestions`.

### Features

- **actions:** generalize request actions
- **actions:** use `cancellable-promise` in every request action
- **animations:** add `CollapseHeight` component
- **base-components:** add `BaseFilters` component
- **base-components:** add `BaseNumberRangeFilter` component
- **base-components:** add `BaseCurrency` component
- **base-components:** add `BaseFiltersSearch` component
- **base-components:** add `BaseHeaderTogglePanel` component
- **base-components:** add `BaseSlicedFilters` component
- **base-components:** add `BaseHierarchicalFilter` component
- **base-components:** add `BaseTogglePanel` component
- **facets:** add `ClearAll` selected filters component
- **eslint:** update `@empathy/eslint-plugin-x` to `1.2.1` and fix some files
- **facets:** add `MultiSelectFilters` component.
- **facets:** add `SelectedFiltersChanged` emitter
- **facets:** add `toggleSimpleFilter` action
- **facets:** all filter button which deselects its filters
- **facets:** add `toggleHierarchicalFilter` action
- **facets:** add new events for clear filters
- **facets:** extract `BaseFilter` component from `BaseHierarchicalFilter` and `BaseSimpleFilter`
  components
- **facets:** add `Facets` component
- **facets:** keep selection state of the current filters
- **facets:** update facets module with new search-types
- **facets:** add `filtersMap` getter and `selectedFilters` getter refactor
- **search:** add `SelectedFiltersChanged` wiring
- **store:** add `status` to every store module
- **utils:** add callback for cancellable promises

### Bug Fixes

- **base-components:** make `BaseTogglePanel` component render `div` to solve react-wrapper
  integration issues.
- **index.html:** added link to polyfill.io to load polyfills necessary for running the project in
  IE
- **jenkinsfile:** Updated Docker image version
- **runbooks-integration:** fix the bug on the sidebar paths doesn't match the real paths
- **search-input:** fix debounced query not cancelled on clear query issue

### Documentation

- **docusaurus:** automated sidebar generation & docusaurus markdown headers.

### Testing

- **e2e:** fix Keyboard Navigation & Base Modal Container e2e tests
- **e2e:** fix some e2e tests adding checks as guards

### Styling

- **base-components:** reformat `BaseFilter` code and add style for selected filters

### Code Refactoring

- **base-components:** rename from figure to picture
- **base-components:** added default content to some simple components and default style

### 1.1.2 (2020-12-03)

### Bug Fixes

- **build:** replace style injector with ES5 version

### 1.1.1 (2020-12-03)

### Bug Fixes

- **build:** output es5 code for Vue components

## 1.1.0 (2020-10-20)

### Features

- **animations:** add staggering-transition-group component
- **api-extractor:** refactor api-extractor doc generation
- **build:** add rollup polyfills wrapper plugin
- **cancellable-promise:** add cancellable-promise utility
- **empathize:** keep Empathize open when focus inside
- **eslint:** update eslint-plugin-x to 1.2.0 version which includes 2.1.2 prettier version
- **facets-empty-module:** create empty module for facets
- **facets-module:** create wire which emits commit to set the facets in the state
- **getters-query-suggestions:** create getters for query suggestions to use property
  hideIfEqualsQuery
- **popular-searches:** add hide popular searches that have already been searched in session
- **search:** add basic search x-module
- **search-input:** add property autofocus
- **sliding-panel:** add SlidingPanel component
- **x-installer:** add XInstaller utility

### Bug Fixes

- **clean-search-input:** add emitter for the `UserClearedQuery` event. Allow `UserIsTypingAQuery`
  to be always emitted.
- **history-queries:** fixed toggle related tag action to clean the previous related tags
- **identifier-results:** fix the request action to save the results if the query is empty

### Documentation

- **build:** document how to debug the build process
- **xcomponents:** move xcomponents documentation to independent file. Added header to each file

### Testing

- **e2e:** create multiple test environment templates
- **e2e:** define basic use cases
- **result-image:** e2e tests for the component

## 1.0.0 (2020-07-30)

### Features

- **base-suggestions:** add index to slot bindings for suggestions
- **config:** refactor XPluginOptions and XModule configurations
- **decorator:** add support for multiple and dynamic events to XOn decorator
- **decorators:** add filtering support to XOn decorator
- **emitters:** add `isDifferent` optional option to emitters for checking if the observed value has
  really changed
- **empathize:** add empathize component
- **getters-proxy:** add cache to the getters proxy
- **identifier-results:** add IdentifierResult component
- **identifier-results:** add mutations and actions to the module
- **identifier-results:** create identifier results module with getters
- **identifier-results:** identifierResults component and module wiring
- **linter:** add x eslint plugin
- **next-queries:** add maxItemsToRender prop
- **wiring:** add option to pass function with the store as payload for the wireDispatch factory
  methods.
- **wiring:** refactor namespaced wiring
- **wiring:** refactor namespaced wiring
- **x-plugin:** add alias API
- **currency-filter:** add currency filter and formatter
- **base-result-previous-price:** add base result previous price component
- **related-tags:** add e2e testing for the related tags
- **spatial-navigation:** ability to move between any component and the keyboard-navigation
  component
- **animations:** fade and slide animation component
- **base-modal-container:** add base-modal-container component
- **base-result-current-price:** create base result current price component
- **base-result-image:** add the base result image with lazy loading also fallback and placeholder
- **base-result-link:** refactor BaseResultLink component to receive origin and events by injection
- **base-suggestion:** allow string in matching part to retain accent marks
- **bus:** make metadata parameter optional
- **clear-search-input:** add clear-search-input button
- **close-button:** add close-button component
- **compile-message:** add compileMessage filter and register it globally
- **conventional-commits:** add conventional-commits and commitizen npm packages
- **cypress:** add @cypress/webpack-preprocessor to support TypeScript
- **cypress:** add custom command for cypress
- **cypress:** disable video recording in Cypress e2e tests
- **cypress:** inject XComponents to the global window object when Cypress is running
- **docs:** docusaurus integration
- **empathize:** create empty Empathize module
- **empathize:** keyboardNavigation component which deals with arrow keys pressed inside it
- **eslint:** configure ESLint by subfolder and cypress rules
- **event-button:** add metadata target property to emitted events
- **event-metadata:** add metadata parameter
- **eventbutton:** add EventButton reusable component
- **global-config:** add global configuration XConfig
- **history-queries:** add actions
- **history-queries:** add ClearHistoryQueries Component
- **history-queries:** add delete-history-query component
- **history-queries:** add DeleteHistoryQuery component
- **history-queries:** add history queries emitters
- **history-queries:** add history queries getters
- **history-queries:** add history queries module wiring.
- **history-queries:** add history queries store for its x-module
- **history-queries:** add history queries x-module skeleton
- **history-queries:** add history-queries module to app & its e2e testing
- **history-queries:** add HistoryQueries component
- **history-queries:** add load history queries action
- **history-queries:** add module events
- **history-queries:** trim query before storing it
- **immediate-store-emitters:** add immediate option for store emitters configuration
- **keyboard-navigation:** add SpatialNavigation service to use in keyboard navigation component
- **next-queries:** add config for the next queries module
- **next-queries:** add events types for the next queries module
- **next-queries:** add Next Queries Component
- **next-queries:** add next-queries x-module
- **next-queries:** add NextQueriesChanged emitter to next queries emitters
- **next-queries:** add NextQueriesChanged emitter to next queries emitters
- **next-queries:** add the NextQuery component
- **no-suggestions:** append no-suggestions component
- **no-suggestions:** append store, configuration, wiring and skeleton no-suggestions x-module
- **open-button:** add open-button component
- **popular-searches:** add config to popular-searches x-module
- **popular-searches:** add popular-searches x-module
- **popular-searches:** append popular searches x-modules events
- **popular-searches:** append PopularSearch component
- **prettier:** add prettier-organize-imports plugin
- **pure-suggestion:** add base suggestion to reuse in every suggestion type
- **query-suggestions:** add query suggestions events
- **query-suggestions:** add query-suggestion component
- **query-suggestions:** add query-suggestions component
- **query-suggestions-actions:** refactor actions to an independent files and add test
- **query-suggestions-getters:** refactor getters in separated files and testing
- **query-suggestions-wiring:** add query suggestions wiring
- **recommendations:** create recommendations x-module
- **recommendations:** recommendations actions, getters & mutations
- **recommendations:** recommendations component and its test
- **recommendations:** recommendations wiring, emitters and events
- **related-tags:** add empty related tags module
- **related-tags:** add mutations and getters for the related tags module. Add testing for getters
- **related-tags:** add related tags actions and testing
- **related-tags:** add related tags state
- **related-tags:** add wiring and emitters for the related tags
- **related-tags:** add related-tags component
- **related-tags:** add the selected related tags to the request
- **result-add-to-cart:** add BaseResultAddToCart component
- **result-link:** create BaseResultLink component and events associated with it
- **sanitize:** add sanitize function to encode characters in string
- **search-box:** add event UserClearedQuery to be emitted when search-box is cleared in any way
- **search-box:** add instant search to SearchInput component
- **search-box-config:** add default config for search-box x-module
- **search-box-module-events:** add new events of search-box module
- **search-box-wiring:** add wires in search-box wiring
- **search-button:** add search-button component
- **search-input:** add search input component
- **search-types:** include the search-types.api.json file to generate the package documentation
- **standard-version:** append ci type into standard version configuration
- **suggestions:** add suggestions generic component
- **term-suggestions-config:** add term-suggestions config
- **test-utils:** add utility functions to make easier testing with jest
- **ts-doc:** add support to tsdoc and jsdoc eslint plugins
- **ts-es-lint:** add support to TypeScript ES-lint through new plugin
- **utils:** add array and normalize shared utility functions
- **utils:** add debounce util
- **vue-styleguidist:** add vue styleguidist to document components
- **wires-factory:** add implementation to NamespacedWireFactory.wireCommit with function payload
- **wiring:** add WirePayloadParams type and modified NamespacedWireFactory
- **wiring:** allow wiring operators to access store to retrieve data
- **wiring-operators:** add filterWhitelistedModules & filterBlacklistedModules operators
- **x-api:** append X API and installX middleware function to install X
- **x-component.utils:** add `getXComponentXModuleName` util function
- **x-plugin:** add logic to save component configurations to store
- **xon-decorator:** add XOn decorator to handle the subscription/unsubscription of an XEvent
- **xplugin-search-adapter:** extract adapter to XPlugin and add subscription to
  adapterConfigChanged
- **wiring:** add `createWireFromFunction` wire factory function. Add `filter`,
  `filterTruthyPayload`, `filterFalsyPayload`, `debounce` & `throttle` wire operator functions
- **bus:** remove circular dependency from `BaseXBus` and Vue components. Make bus emit only from
  root component.
- **build:** add rollup build
- **decorators:** add type safe `State` and `Getter` decorators for accessing state and getters in
  class components
- **term-suggestions:** add term-suggestions x-module skeleton
- **search-box:** add search-box x-module skeleton
- **typing:** remove unnecessary `XStoreTree` type
- **x-module:** add `withModule` function to create `XModule` scoped wires
- **x-module:** remove `Emitters` and `Wiring` generic types from `XModule`
- **store:** add Store and StoreEmitters to the X-Module
- **wiring:** add wiring system
- **wiring-factory:** add wiring factory methods
- **project:** create project with basic shared utils

### Bug Fixes

- **wire-operators:** handle race events for the debounce wire operator
- **spatial-navigation:** filter out focusable elements if they can't be focused
- **build:** make build fail if api-extractor has errors
- **components:** fix vue components exports
- **cypress:** fix Cypress webpack/preprocessor config to avoid .ts transpilation file issues
- **debounce:** remove wireDebounce to avoid side effects
- **history-queries:** fix class selector in history queries' e2e test
- **history-queries:** fix history queries removing queries when replacing last stored query
- **jenkins:** add test command for Jenkins CI
- **jest:** fix testMatch option to look into src instead all project
- **next-queries:** avoid clearing next-queries when the query is empty
- **query-suggestion:** use getter of normalizedQuery to use as query in the component
- **query-suggestions:** fix missing css class, slots docs, slot naming to kebab case and binds
- **request-getters:** avoid constructing request when the query is empty or has spaces
- **rxjs:** fix rxjs imports to support rollup commonjs plugin
- **storage-service:** add dummy local storage service for node environment
- **tests-fix:** fix tests making them wait until Vue updates reactive dependencies
- **types:** fix store generic type constraint for Mutations and Actions
- **vue-styleguidist:** create props template to overwrite the default styleguidist template
- **vue-styleguidist:** create vue-docgen slots template to overwrite the default one. Close tags
  within the documentation between backslashes.
- **x-plugin:** make immediate emitters async
- **x-plugin.mixin:** refactor $x to get root XComponent inside bus emit

### Continuous Integration

- **package.json:** configure E2E tests command for CI Jenkins integration

### Documentation

- **docs:** add static md file to be copied to docs folder on build proccess
- **slots:** fix slot and binding documentations for vue styleguidist
- **docs:** update the folders structure to create the static-docs and live examples
- **api-extractor:** add API Extractor to generate the documentation
- **api-extractor:** add missing api extractor marks
- **docgen.config:** fix the naming of the md files generated from components
- **history-queries:** fix remove-history-query doc link

### Testing

- **keyboard-navigation:** e2e testing for keyboard-navigation
- **base-modal-container:** add e2e test to base-modal-container component
- **e2e-popular-searches-tests:** add e2e test for popular-searches
- **next-queries:** add e2e test for next queries
- **no-suggestions:** add e2e tests
- **x-plugin:** fix tests to use the installNewXPlugin helper

### Code Refactoring

- **base-components:** refactor open and close button components so they're reusable
- **tests:** update vue-utils-test version and fix test
- **base-components:** remove pure folder and refactor base components names
- **bem-css-classes:** refactor css classes following BEM
- **bus:** replaced `Subject` with `ReplaySubject`
- **extractstate & extractgetters types:** refactor ExtractState and ExtractGetters types
- **history-queries:** move history queries to the root utils folder
- **history-queries:** refactor removeFromHistory action to accept `HistoryQuery` instead of an
  string
- **history-queries:** rename DeleteHistoryQuery to use keyword `remove`
- **next-queries:** move actions to an independent folder
- **next-queries:** move getters to an independent folder
- **next-queries:** refactor the next-queries x-module that was already created
- **popular-searches:** extract getters from module
- **popular-searches:** extract module actions to an independent files
- **popular-searches:** refactor slot and state names, update docs and refactor variable in test
- **query-suggestions:** rename term-suggestions to query-suggestions
- **search-input:** refactor to use XOn decorator instead of creating manually subscription
- **x-plugin:** extract getters Proxy creation from XPlugin
- **x-plugin:** remove global messages object in favour of individual messages
- **x-plugin:** remove x-plugin singleton and improve testability
- **xevents:** refactor XEvents into their respective module
- **rxjs:** remove rxjs-compat and amend the imports

### Build System

- **dependencies:** set minimum supported versions of Vue and Vuex dependencies
- **browserslist:** add browserslist configuration
- **dependencies:** update `@empathy` dependencies
- **dependencies:** update dependencies to match with the rest of the projects
