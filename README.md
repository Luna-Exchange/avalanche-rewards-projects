# Onboarding Missions

## Introduction to Avalanche Rewards

Avalanche Rewards is a loyalty rewards system designed for projects built on top of the Avalanche blockchain. By onboarding missions to Avalanche Rewards, you can offer users additional value and increase engagement within your project's ecosystem.

## Onboarding Your Missions

The process for getting your missions live on Avalanche Rewards is as follows:

1. **Mission Design**: Create your mission using the JSON format described below.

2. **Pull Request (PR) Submission**: Once your mission JSON is ready, submit it as a PR to our GitHub repository. For partners, use the partners folder; for non-partners, use the non-partners folder.

3. **Review Process**: The team at Insomnia Labs will review your submission. We may contact you if we need clarifications or have suggestions to enhance your mission.

4. **Launch**: Upon approval, we'll merge your PR, and your mission will go live on Avalanche Rewards.

## Mission JSON Structure

Your mission JSON is the core of your Avalanche project. Here's a breakdown of its structure:

### Basic Information
```json
{
  "name": "Your Brand Name",
  "description": "A concise description of your project",
  "imgUrl": "A link to your logo or representative image"
}
```

### Mission Details
```json
"missions": [
  {
    "name": "YOUR_MISSION_NAME",
    "description": "Description of the mission",
    "imgUrl": "An image representing this mission",
    "projectUrl": "Link to more information about this project",
    "tags": ["NFT", "DeFi", "Gaming"],
    "total_points_reward": 100,
    "quests": [ ... ],
    "badge": { ... }
  }
]
```

### Quests
```json
"quests": [
  {
    "name": "Quest Title",
    "description": "Description of the quest",
    "category": "NFT, DeFi, or Gaming",
    "contract_address": "The contract address of the token the quest is on",
    "frequency":"one_time", // "daily" for the daily missions
    "rewards": [
      {
        "type": "points",
        "value": 50
      }
    ],
    "tasks": [ ... ]
  }
]
```

### Tasks
```json
"tasks": [
  {
    "name": "Task Name",
    "type": "MINT, SWAP, STAKE, etc.",
    "description": "Description of the task",
    "contract_address": "The contract address of the token the task is on",
    "chain_id": "The unique identifier of the avalanche subnet where the smart contract is deployed, this defaults to 43114 (Avalanche C-Chain)",
    "metadata": {"threshold":0},
    "method_id": "The hashed event signature of the function that carries the action for the task",
    // OR
    "method_ids": ["0xhashed_event_signature1", "0xhashed_event_signature2"]
  }
]
```

### Badges
```json
"badge": {
  "name": "Badge Name",
  "description": "Description of the badge",
  "imgUrl": "Link to the badge image"
}
```

## Examples

### NFT Mission: Dokyo
```json
{
    "name": "Dokyo",
    "description": "Dokyo is an NFT collection on the Avalanche network, with approximately $30 million in trading volume in January 2024.",
    "imgUrl": "https://i.seadn.io/s/raw/files/e244879af1a5732c8260f41b414ce8b9.png?auto=format&dpr=1&w=1000",
    "missions": [
        {
            "name": "DOKYO_COLLECTOR",
            "description": "Complete this NFT collection mission",
            "imgUrl": "https://i.seadn.io/s/raw/files/e244879af1a5732c8260f41b414ce8b9.png?auto=format&dpr=1&w=1000",
            "tags": [
                "NFT"
            ],
            "quests": [
                {
                    "name": "Dokyo Genesis",
                    "description": "Acquire your first Dokyo NFT",
                    "category": "NFT",
                    "frequency":"one_time",
                    "contract_address": "0x54c800d2331e10467143911aabca092d68bf4166",
                    "rewards": [
                        {
                            "type": "points",
                            "value": 60
                        }
                    ],
                    "tasks": [
                        {
                            "name": "Mint Dokyo",
                            "type": "MINT",
                            "description": "Mint your first Dokyo NFT",
                            "contract_address": "0x54c800d2331e10467143911aabca092d68bf4166",
                            "method_id": "0xd37c353b",
                            "metadata": {"threshold":0},
                            "chain_id": "43114"
                        }
                    ]
                }
            ],
            "total_points_reward": 60,
            "badge": {
                "imgUrl": "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQA7r8VBZTrhn1OZPjJh-8Ac9mV06FA6uupYJVZAnGc7g&s",
                "name": "Dokyo Collector",
                "description": "Awarded for completing the Dokyo collection mission"
            }
        }
    ]
}
```

### DeFi Mission: Pangolin
```json
{
    "name": "Pangolin",
    "description": "Pangolin is a decentralized exchange (DEX) on the Avalanche network.",
    "imgUrl": "https://s2.coinmarketcap.com/static/img/coins/64x64/8422.png",
    "missions": [
        {
            "name": "PANGOLIN_SWAP",
            "description": "Complete a swap on Pangolin DEX",
            "imgUrl": "https://s2.coinmarketcap.com/static/img/coins/64x64/8422.png",
            "tags": [
                "DeFi"
            ],
            "quests": [
                {
                    "name": "First Swap",
                    "description": "Execute your first swap on Pangolin",
                    "category": "DeFi",
                    "contract_address": "0x60781C2586D68229fde47564546784ab3fACA982",
                    "rewards": [
                        {
                            "type": "points",
                            "value": 60
                        }
                    ],
                    "tasks": [
                        {
                            "name": "Perform Swap",
                            "type": "SWAP",
                            "description": "Complete a token swap on Pangolin",
                            "contract_address": "0xE54Ca86531e17Ef3616d22Ca28b0D458b6C89106",
                            "chain_id": "43114",
                            "method_ids": ["0xd37c353b", "0x42842e0e"]
                        }
                    ]
                }
            ],
            "total_points_reward": 60,
            "badge": {
                "name": "Pangolin Trader",
                "description": "Awarded for completing a swap on Pangolin",
                "imgUrl": "https://s2.coinmarketcap.com/static/img/coins/64x64/8422.png"
            }
        }
    ]
}
```

## Best Practices for Mission Creation

When designing your mission, consider the following:

- **Clarity**: Ensure your descriptions are clear and easy to understand.
- **Uniqueness**: Highlight what makes your project unique.
- **Categories**: Remember that tags and categories can only be "NFT", "DeFi", or "Gaming".
- **Method IDs**: Use `method_id` for a single method and `method_ids` for multiple methods. Choose based on your task requirements.

## Updating Your Missions

To update an existing mission:

1. Locate your mission's JSON file in the repository.
2. Make the necessary changes to the mission details, quests, or tasks.
3. Submit a new Pull Request with your changes.
4. In the PR description, clearly explain the updates you've made.
5. The Insomnia Labs team will review your changes and merge them if approved.

## Support

If you encounter any issues or have questions about creating or updating your missions:

1. Check the existing issues in the GitHub repository to see if your question has already been addressed.
2. Create an issue.

The Insomnia Labs team will respond to your issue as soon as possible.

