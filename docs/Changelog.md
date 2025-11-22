# Changelog

## 22/11/2025, 23:35 pm - Demo Banner Hidden After Exit

- **Problem:** After users left the demo using the door icon, the yellow demo warning banner would still appear on every page load, confusing users who had already chosen to start fresh with their own data.
- **Solution:** Implemented a persistent state to track when users have exited the demo, automatically hiding the demo banner after they choose to clear their board and start fresh.
- **Implications:** Provides a cleaner user experience by removing unnecessary demo warnings for users who have already decided to start with their own empty board, while maintaining the demo banner for new users.
- **Implemented Changes:**
  - Added `hasExitedDemo` state with localStorage persistence (`ideaFlowHasExitedDemo`)
  - Modified demo banner rendering to conditionally show only when `hasExitedDemo` is false
  - Updated `clearBoard()` function to set `hasExitedDemo` to true when users clear their data
  - Added corresponding `useEffect` to save `hasExitedDemo` state to localStorage
- **Files Modified:** [`index.html`](index.html)
- **Git Branch:** main

## 22/11/2025, 23:16 pm - Added Demo Exit Door Icon

- **Problem:** Users needed an intuitive way to exit the demo mode and clear all data to start fresh with their own projects, but the "Clear Board" button was not prominently visible or immediately obvious for new users encountering the demo banner.
- **Solution:** Added a door exit icon (🚪) on the extreme left of the demo warning banner that triggers the same comprehensive reset dialog as the "Clear Board" button, providing a clear visual cue for exiting the demo.
- **Implications:** Enhances user experience by making the "exit demo" action more discoverable and intuitive, while maintaining all existing safety warnings about data loss.
- **Implemented Changes:**
  - Added clickable door SVG icon with arrow pointing into it, positioned left of demo text
  - Icon uses yellow color matching banner theme, with red hover effect indicating destructive action
  - Reuses existing `showResetDialog` state to show the same detailed warning dialog
  - Added proper tooltip "Exit Demo - Clear All Data" for accessibility
- **Files Modified:** [`index.html`](index.html)
- **Git Branch:** main
- **Lessons Learned:** Reusing existing UI components and state management reduces code complexity and maintains consistent behavior across different user interaction paths.
This document tracks notable changes made to the IdeaFlow project.

## 22/11/2025, 11:14 pm

- **Problem:** The .gitignore file was minimal and didn't cover essential web development files, and the favicon files existed but weren't properly referenced in the HTML.
- **Solution:** Enhanced .gitignore with comprehensive patterns and added complete favicon links to the HTML head section.
- **Implications:** Improved project hygiene by preventing unnecessary files from being committed, and proper favicon implementation enhances branding and professional appearance.
- **Implemented Changes:**
  - **Enhanced .gitignore:** Added patterns for:
    - OS generated files (.DS_Store, Thumbs.db, etc.)
    - Editor directories and files (.vscode/, .idea/, *.swp)
    - Python cache files (__pycache__/, *.pyc)
    - JavaScript/Node.js (node_modules/, npm-debug.log*)
    - Build outputs (dist/, build/, *.tgz)
    - Environment files (.env*, logs/)
    - Temporary files (*.tmp, *.temp)
    - Development tools (.sass-cache/, .cache/)
    - Archive files (*.zip, *.rar)
  - **Added favicon links:** Added comprehensive favicon support including:
    - Main favicon (.ico format)
    - PNG variants (32x32, 16x16)
    - Apple touch icon (180x180)
    - Android icons (192x192, 512x512)
    - Web app manifest
- **Files Modified:** [`.gitignore`](.gitignore), [`index.html`](index.html)
- **Git Branch:** main

## 22/11/2025, 10:20 pm

- **Problem:** Users needed a way to completely reset their project board to clean demo data, but there was no clear mechanism to do so with proper warnings about data loss.
- **Solution:** Added a comprehensive reset button with explicit data loss warnings and multiple confirmation steps.
- **Implications:** Users can now safely reset their board to start fresh with demo data, with clear understanding of what will be lost.
- **Implemented Changes:**
  - Added red "Reset Board" button positioned next to "Add Idea" button for intuitive UI flow
  - Created detailed confirmation dialog showing exactly what data will be lost:
    - All projects currently on the board
    - All project details, descriptions, and full descriptions
    - All progress tracking and completion percentages
    - All tags and categories
    - All subtasks and their completion status
    - All custom project modifications
  - Implemented double confirmation system (custom dialog + browser confirm)
  - Added backup recommendation before reset
  - Created reset function that clears localStorage and reloads page to restore default demo data
- **Files Modified:** [`index.html`](index.html)
- **Git Branch:** main

## 29/05/2025, 1:05 am

- **Problem:** The website had limited mobile accessibility, specifically small touch targets for interactive elements and missing focus indicators.
- **Solution:** Implemented changes to increase the touch area of the edit and delete buttons in the `ProjectCard` component and restored default focus outlines for improved keyboard navigation.
- **Implications:** Enhanced usability and accessibility for users accessing the application on mobile devices and those using keyboard navigation.
- **Implemented Changes:** Added `p-2` Tailwind class to the edit and delete buttons in `index.html` and removed the `focus:outline-none` class from these buttons.
- **Files Modified:** [`index.html`](index.html), [`docs/mobile_accessibility_plan.md`](docs/mobile_accessibility_plan.md)
- **Git Branch:** main