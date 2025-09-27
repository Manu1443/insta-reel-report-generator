# insta-reel-report-generator
import matplotlib.pyplot as plt
from matplotlib.patches import Rectangle

# Sample data for mock Reel review
data = {
    "Views": 13575,
    "Watch Time": "14h 40m 40s",
    "Interactions": 910,
    "Profile Activity": 1,
    "View Rate (First 3s)": "75.0%",
    "Avg Watch Time": "7 sec",
    "Followers %": 27.7,
    "Non-followers %": 72.3,
    "Sources": {
        "Reels tab": 49.1,
        "Stories": 19.8,
        "Explore": 18.8,
        "Feed": 11.0,
        "Profile": 0.6,
    },
    "Likes": 900,
    "Shares": 306,
    "Saves": 219,
    "Comments": 25,
    "Accounts Reached": 4626,
    "Accounts Engaged": 391
}

# Create figure
fig, ax = plt.subplots(figsize=(10, 6))
ax.axis('off')

# Draw header
ax.add_patch(Rectangle((0, 0.85), 1, 0.15, color='#121212'))
ax.text(0.5, 0.92, 'Instagram Reel Insights Summary',
        ha='center', fontsize=14, weight='bold', color='white')

# Metrics block
metrics = f"""Views: {data['Views']}
Watch Time: {data['Watch Time']}
Average Watch Time: {data['Avg Watch Time']}
Interactions: {data['Interactions']}
Likes: {data['Likes']}  Shares: {data['Shares']}  Saves: {data['Saves']}  Comments: {data['Comments']}
Accounts Reached: {data['Accounts Reached']}
Accounts Engaged: {data['Accounts Engaged']}
Follower Views: {data['Followers %']}%  |  Non-Follower Views: {data['Non-followers %']}%
View Rate (First 3s): {data['View Rate (First 3s)']}
Profile Activity (Follows): {data['Profile Activity']}"""

ax.text(0.02, 0.75, metrics, fontsize=11, va='top', color='white')

# Source Breakdown Pie Chart
sources = data['Sources']
labels = list(sources.keys())
sizes = list(sources.values())

plt.axes([0.55, 0.05, 0.4, 0.4])  # x, y, width, height
plt.pie(sizes, labels=labels, autopct='%1.1f%%', startangle=140,
        textprops={'color': 'white'})
plt.title('Top Sources of Views', color='white')

# Set dark background
fig.patch.set_facecolor('#000000')

# ✅ Save to a valid Windows path
output_path = r"C:\Users\manoj\OneDrive\Desktop\python11\insta_reel_insight_mockup.png"
plt.savefig(output_path, dpi=200, bbox_inches='tight', facecolor=fig.get_facecolor())
plt.show()

print(f"✅ Image saved successfully to:\n{output_path}")

