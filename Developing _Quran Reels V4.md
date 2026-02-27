Create a high-end web application to generate Quranic Reels. The app must fetch background videos from specific \*\*curated collections\*\* to ensure visual quality, use \*\*AI\*\* for context matching, and \*\*Remotion\*\* for professional MP4 rendering (solving the 00:00 duration/metadata issue).

\*\*Technical Stack:\*\*  
\- \*\*Framework:\*\* Next.js 14+ (App Router), TypeScript, Tailwind CSS.  
\- \*\*Video Engine:\*\* Remotion (@remotion/player, @remotion/renderer).  
\- \*\*AI:\*\* Google Gemini 1.5 Flash (to analyze verses and match them with the best video from the collections).  
\- \*\*Media Sources (Strict Priority):\*\*  
    1\.  \*\*Pexels API:\*\* Key: \`kcGUOqBqL2T4hmzu3YAguXBcyhDtKhnTvfmzQgzUJpD8DOmJO67OF6iC\`.   
        \- \*\*Target:\*\* Fetch videos from Collection ID: \`quran\_backgrounds-ynfjbj8\`.  
    2\.  \*\*Pixabay API:\*\* Key: \`14705796-47bceaabbb521b2ff50a3ee95\`.  
        \- \*\*Target:\*\* Fetch videos from Collection ID/Search: \`quran-background-32048070\`.  
    3\.  \*\*Local Fallback:\*\* Videos in \`/public/assets/videos/\`.

\*\*Core Functional Logic:\*\*

\*\*1. Curated Media Engine:\*\*  
\- Implement a service \`getMediaAsset(verseMood: string)\`.  
\- \*\*Logic:\*\* Instead of a general search, the app must first fetch the list of videos from the \*\*Pexels Quran Collection\*\*.   
\- \*\*AI Matching:\*\* Gemini should analyze the verse and provide a "Mood" (e.g., "Peaceful", "Powerful", "Dark"). The engine then selects the most appropriate video from the \*\*curated collection\*\* based on this mood.  
\- If the Pexels collection is unavailable, switch to the \*\*Pixabay Quran Collection\*\*.  
\- If both fail, use the local assets folder.

\*\*2. Remotion Video Composition (9:16):\*\*  
\- \*\*Layers:\*\*   
    \- \*\*Background:\*\* Video from the curated collection with a "Ken Burns" (slow zoom) effect.  
    \- \*\*Overlay:\*\* 30% black gradient to ensure text clarity.  
    \- \*\*Arabic Text:\*\* 'Amiri' font, centered, with "Text Reveal" animation synced to audio.  
    \- \*\*Translation:\*\* 'Inter' font, slightly smaller, positioned below the Arabic.  
    \- \*\*Audio Visualizer:\*\* A frequency-reactive wave at the bottom.  
\- \*\*Audio:\*\* Integrate reciter MP3s with frame-accurate synchronization.

\*\*3. Rendering Pipeline:\*\*  
\- Use \`@remotion/renderer\` to process the video.   
\- \*\*Metadata Fix:\*\* Ensure the output is a standard MP4 with \`faststart\` flags so it's ready for instant upload to Instagram/TikTok without the "00:00 duration" error.

\*\*4. UI Components:\*\*  
\- \*\*Sidebar:\*\* Selection of Surah, Ayah range, and Qari.  
\- \*\*Live Preview:\*\* A mobile-frame player using \`@remotion/player\`.  
\- \*\*Export UI:\*\* Progress bar showing the rendering status frame-by-frame.

\*\*Requested Output:\*\*  
1\.  \*\*Project Architecture:\*\* Setup for Next.js \+ Remotion.  
2\.  \*\*Collection Fetching Logic:\*\* TypeScript code to fetch and cache videos from the specific Pexels and Pixabay collections.  
3\.  \*\*The Remotion Composition:\*\* The main React component for the Reel.  
4\.  \*\*AI Integration:\*\* How Gemini picks the "best" video from the fetched collection list.
