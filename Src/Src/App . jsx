import { useState } from "react";

export default function App() {
  const [story, setStory] = useState("");
  const [video, setVideo] = useState("");
  const [loading, setLoading] = useState(false);

  const generateVideo = async () => {
    setLoading(true);
    setVideo("");

    const res = await fetch(
      "https://sora-backend-fixed-1.onrender.com/generate",
      {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ prompt: story }),
      }
    );

    const data = await res.json();
    setVideo(data.video_url);
    setLoading(false);
  };

  return (
    <div style={{ padding: 20 }}>
      <h1>InvideoX</h1>

      <textarea
        rows="5"
        style={{ width: "100%" }}
        placeholder="Apni story yahan likho..."
        value={story}
        onChange={(e) => setStory(e.target.value)}
      />

      <br /><br />

      <button onClick={generateVideo} disabled={loading}>
        {loading ? "Generating..." : "Generate Video"}
      </button>

      <br /><br />

      {video && (
        <video src={video} controls width="100%" />
      )}
    </div>
  );
}
